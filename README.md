# Realtime-Transit-Display

A realtime transit display meant for a kiosk with no user interaction.  It shows realtime arrivals of MUNI and BART transit vehicles for nearby stations, Uber wait times and weather.

## Example

You can see the Realtime Transit Display in use at [transit.bn.ee](http://transit.bn.ee).  A raspberry pi can be used to power the display, [see this post](http://blog.bn.ee/2013/01/11/building-a-real-time-transit-information-kiosk-with-raspberry-pi/).

## Pi Setup

Follow all the regular Pi setup instructions for the the basic kiosk as listed above.  After testing and getting the BART arrival display to work correctly, comment out the '@chromium --kiosk --incognito bart.blinktag.com/?station=16T" with the '#' to prevent the autostart.

## Running

Install an older version 0.10.xx of node.js as sudo pi [as detailed here] (https://ariejan.net/2011/10/24/installing-node-js-and-npm-on-ubuntu-debian/)

    git clone https://github.com/joyent/node.git
    cd node
    git tag # Gives you a list of released versions
    git checkout v0.10.xx
    ./configure
    make
    sudo make install
	
Then, check if node was installed correctly:
	
	node -v
	
Skip their npm install instructions as that script is no longer available.  Use 'apt-get' for npm install.	

	apt-get install npm
	
Then, check if node was installed correctly:
	
	npm -v
	
Install required modules

    npm install
	
Copy the RTTD to your pi directory	
	
	git clone https://github.com/brendannee/Realtime-Transit-Display.git
	
Copy `config-sample.json` to `config.json`

    cp config-sample.json config.json

Add your [wunderground token](http://www.wunderground.com/weather/api/) and [Uber Token](https://developer.uber.com) to `config.json`.

Run the app

    node app.js

## APIs

* [Weather Underground](http://api.wunderground.com)
* [BART API](http://api.bart.gov)
* [NextMUNI API](http://www.sfmta.com/cms/asite/nextmunidata.htm)
* [Uber API](https://developer.uber.com)

## Credits

Brendan Nee me@bn.ee

## License

(The MIT License)

Copyright (c) 2014 Brendan Nee &lt;me@bn.ee&gt;

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
