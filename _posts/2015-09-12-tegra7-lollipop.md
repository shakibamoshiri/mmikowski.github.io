---
layout: post
title: Fixing Lollipop 5.1 on the EVGA Tegra Note 7?
---
*OTA 3.0 Screwed the pooch*

![Tegra Note 7 and stylus pimp for the camera][1]

### The problem
When my wife and I first updated our [EVGA Tegra Note 7][2] to Lollipop we found this once very-fast, cool, and battery-sipping tablet became unbearably laggy, hot, and power-hungry. 

We found this odd because we own the Shield Portable with the same SoC and 5.1 Lollipop runs *great* on that device.  This is just a guess, but we think the problem of accumulated system or user data slows the little tablet down because the Note 7 only has half the RAM (1GB).  

We tried to resolve our issues by performing a factory reset.  Unfortunately this did not work.  However, we were not beaten yet.  Read on to see how we got our little tablet to work well with Lollipop 5.1.

## Disclaimers
**Important**: This solution is only known to work for my EVGA Tegra Note 7 WiFi model, **TegraNote-P1640** as shown in `Settings > About tablet > Model number`.  **Attempting the solution on a different model could likely brick the device.** There's even a chance attempting the solution on devices *with the same model number* could get bricked.  Proceed at your own risk.

I also encourage readers to review the excellent [XDA ROMS work][3] from William Rogers for alternate solutions that may be a better choice for their model or situation.

### The solution
Our initial intent was to download the OTA 3.0 GMS recovery image from [Nvidia downloads page][4] and install it.  While there is a link for the OTA 3.0.0 ROM, the link is broken, and it is for the P1988/P1988W model. Instead we decided to load the "OTA 2.5" image and then try updating to Lollipop using OTA.  And it worked!

Once we had finished the tablet runs **much** better than the previous Lollipop install.  As an added bonus, if we want to revert to  KitKat 4.4 ("OTA 2.5") - which is an excellent ROM - we can do so in 10 minutes or so. The entire procedure took less than a half hour.  Here are the steps we took:

1. We unlocked the boot loader using the [instructions][6]

2. We then installed the **NVIDIA Tegra NOTE7 GMS Recovery OS Image** (OTA 2.5) from the [Nvidia downloads page][5] per the [instructions][6].  We used the the `root` account on Linux to avoid any device access permissions issues.  Once we flashed all the images using the `flash-all.sh` script, we had to select `continue` on the tablet's bootloader menu and press the power button to continue with the update.

3. When we signed-in for the first time we disabled `BACKUP & RESTORE` to minimize update time.  We also disabled the `For improved accuracy ...` option to maximize battery life.

4. Once our initial sign-in was complete, we allowed automatic updates to proceed. It took about 15 minutes for all apps to update. We had to approve 5 of them. Because we had disabled `BACKUP & RESTORE` earlier, we probably saved time by avoiding downloading and updating data and applications.

5. Immediately after all updates were applied, we clicked on the OTA 3.0 update in the top-left corner of the screen and pressed `Restart and Install`.

6. After the OTA was complete - in other words, Android 5.1 had been installed - we went to `Settings > Backup & Reset` and enabled `Back up my data` and `Automatic restore`.  We also created a power-control shortcut using [these instructions][7]. We optimized all apps, and we turned off WiFi during sleep. **This is important to maximize battery life and reduce heat**! 

7. We found that **adding a second account** reduced performance noticeably.  This is probably due to the limited RAM.  Just to be safe, we repeated this procedure using my wife's account as the primary and only account.

We have found the upgrade to be very much improved.  The tablet is responsive and cool. The battery life is good again, and it charges completely in under 2 hours (using a Shield charger).

### Parting thoughts

One thing we really appreciate about Nvidia is that they *usually* provide some of the best Android support outside of the Google Nexus program and Motorola. Our family have no carrier contracts and we own all of our Android phones and tablets - Nvidia, Nexus, Moto, ASUS, and EVGA devices, in that order.

So we were really jazzed about the Tegra Note 7 getting the Lollipop upgrade because it had been overlooked for the last year. It's too bad that we had to wrestle with the problem, which we suspect affects the early adopters more than recent purchasers - there is some evidence that more recent Tegra Notes perform very well after the OTA to Lollipop. We wish Nvidia would do a bit more to *own* this problem, because as the above experience shows, they are so close to having a really great update for everyone.


I hope you found this useful, or at least interesting!

Cheers, Mike

[1]:/images/NVIDIA-Tegra-Note-7-420x240.png
[2]:http://www.nvidia.com/object/evga-tegra-note-tablet.html
[3]:http://forum.xda-developers.com/nvidia-tegra-note-7/general/nvidia-tegra-note-7-apx-images-t3149839
[4]:https://developer.nvidia.com/gameworksdownload
[5]:https://developer.nvidia.com/gameworksdownload
[6]:https://developer.nvidia.com/sites/default/files/akamai/mobile/docs/HowTo-Flash-TN7-Recovery-Image.txt
[7]:http://forum.xda-developers.com/nvidia-tegra-note-7/general/attention-how-to-to-power-control-menu-t3164381
