# fire-effect
A fire effect for your Halloween pumpkin using a Pimoroni Blinkt!
If you’d like to create your own pumpkin light effect, you'll need:
<ul>
 	<li>A Raspberry Pi (Make sure you use one that fits in your pumpkin!)</li>
  <li>A SD or microSD card for the OS
 	<li><a href="https://shop.pimoroni.com/products/blinkt">A Pimoroni Blinkt!</a></li>
 	<li>A power supply (plus monitor, mouse, and keyboard for setup, Wifi dongle & adapter (for Zero < W))</li>
 	<li>A pumpkin</li>
</ul>
<p class="p1"><span class="s1">Take your Blinkt! and attach it to your Pi. If you’re using a 1-3-4 model, this will be easy enough, but make sure the Pi fits in your pumpkin!

If, like me, you need/want to go smaller, you might need to solder your header pins to a Zero or Zero W or get alternatively get a Zero WH  which already has the header attached.  Next then attach the Blink! to Pi.</span></p>

Download Raspbian from here https://www.raspberrypi.org/downloads/raspbian/ as we are going to run headless you only need the lite version

NB If your using a Zero pre W then you'll need to add your Wifi dongle using a <a href="https://shop.pimoroni.com/products/usb-to-microusb-otg-converter-shim"> shim</a> or <a href="https://shop.pimoroni.com/products/usb-to-micro-usb-a-adapter"> micro USB to Type F USB</a>

To pre-config wifi you can create a file on a computer called

<pre>wpa_supplicant.conf</pre>

If you have file extensions hidden it may show as a text file. Edit as required, from the sample below

<pre>country=XX
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    scan_ssid=1
    ssid="Your Wifi Name"
    psk="Your Wifi's Password"
}</pre>

Replace XX with your country code, it is a two letter like, GB for the UK, US for the United States, FR for France, BE for Belgium, etc.  Search the net if you don't know yours.  Also make sure you put your Wifi name and password, always include quote marks.

Copy this to the Boot drive of the sd card, Tip it's the drive with start.elf, bootcode.bin, etc

Next create a blank file and save as <pre>ssh</pre> and save again to the Boot drive of the sd card.

Hopefully with all this you can plug in the Pi, after a while the green LED will stop flashing.

If all went well, you will be able to SSH into the device from a computer, Putty for Windows/Linux or native on a mac.

All good, if the above seems too hard, maybe download the Desktop version of Raspbian, you can switch it to boot to the CLI after you've confugure the Wifi and SSH options.

 <p class="p1"><span class="s1">In the terminal, you’ll need to install <a href="https://learn.pimoroni.com/tutorial/sandyj/getting-started-with-blinkt">the Pimoroni Blinkt! library</a>. Use the following to achieve this:</span></p>

<pre>curl -sS get.pimoroni.com/blinkt | bash</pre>
You'll need to reboot the Raspberry Pi to allow the changes to take effect. You can do this by typing:
<pre>sudo reboot</pre>
<p class="p1"><span class="s1">At this point, you’re more than welcome to go your own way with the <a href="https://shop.pimoroni.com/products/blinkt">Blinkt!</a> and design your own light show (<a href="https://learn.pimoroni.com/tutorial/sandyj/getting-started-with-blinkt">this may help</a>). However, and with major thanks to <a href="https://twitter.com/jonic">Jonic Linley</a>, we’ve created a pumpkin fire effect for you.</span></p>
<p class="p1"><span class="s1">Within the terminal, type:</span></p>

<pre>git clone https://github.com/AlexJrassic/fire_effect.git</pre>
This will bring the code to your Raspberry Pi from GitHub. Next, we need to tell the Raspberry Pi to automatically start the fire_effect.py code when you power up. To do this, type:
<pre>sudo crontab -e/pre>
<pre>choose nano</pre>
At end of the file, add this line:
<pre>@reboot sudo python /home/pi/fire_effect/fire_effect.py @</pre>
Save and then reboot:
<pre>sudo reboot
</pre>
<p class="p1"><span class="s1">Now you’re good to go. </span></p>
<p class="p1"><img class="aligncenter wp-image-26300 size-large" src="https://www.raspberrypi.org/wp-content/uploads/2016/10/IMG_9917-e1477571770975-500x500.jpg" alt="Halloween Pumpkin AFTER" width="500" height="500" /></p>
<p class="p1"><span class="s1">To add more of a spread to the light effect, I created a diffuser to cover the Blinkt! LEDs. In the video (https://www.youtube.com/watch?v=YrlezeYjdu0), you’ll see I used a tissue. I wouldn’t suggest this for prolonged use, due to the unit getting a little warm; I won’t be responsible for any  subsequent tissue fires. I would suggest using a semi-opaque bowl (the ones you get a Christmas pudding in) or a piece of plastic from a drinks bottle, and go to town on it with some fine sandpaper.</span></p>
<p class="p1">We also drilled a small hole in the back for the micro-USB lead to reach the Zero. I used a battery pack for power, but you could use a lead directly into the mains. With a larger pumpkin, you could put a battery pack inside with the Pi.</p>
