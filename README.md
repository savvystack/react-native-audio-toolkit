A quick note about this fork
----------------------------
I was using the 2.0.3 release thru NPM in an iOS app, where audio recordings are played
alone with the matching transcripts. I found that the timing between the audio and transcript
was always off, sometimes by as much as 20 seconds in a 30-minute recording. Upon deeper investigation,
I found that the underlying iOS component `AVPlayer` by default doesn't report precise timing during playback. An 
[option](https://developer.apple.com/documentation/avfoundation/avurlassetpreferprecisedurationandtimingkey?language=objc) can be turned on when creating the audio asset to achieve high precision.

So a quick change was made on this fork. I'd like to play around with the change a bit more to see
if it causes any noticable delay during initialization. If all is well, I'll consider submitting a PR.

If you are struggling with the same problem, give this a try.

Here is how you can use the amended version:

```
# remove your existing react-native-audio-toolkit NPM package
npm install git://github.com/savvystack/react-native-audio-toolkit#ios-precise-duration-and-timing --save
# or
yarn add git://github.com/savvystack/react-native-audio-toolkit#ios-precise-duration-and-timing
```


![banner](/banner.png)

[![npm version](https://badge.fury.io/js/%40react-native-community%2Faudio-toolkit.svg)](https://badge.fury.io/js/%40react-native-community%2Faudio-toolkit)

This is a cross-platform (Android and iOS) audio library for React Native.
Both audio playback and recording is supported. In addition to basic
functionality, many useful features are implemented such as seeking,
looping and streaming audio files over the network.

An example how to use this library is included in the [ExampleApp](/ExampleApp)
directory. The demo showcases most of the functionality that is available, with
documentation under [docs](/docs). In the simplest case, playing media is as
easy as:

```js
new Player('filename.mp4').play();
```

and recording media to filename.mp4 similarly
```js
new Recorder(‘filename.mp4’).record();
```

How to get this stuff running?
------------------------------

* For a quick test drive, check out the [demo application](/ExampleApp)
* [Include the library](/docs/SETUP.md) in your project

Documentation
-------------

* Find the API documentation [here](/docs/API.md)
* Examples on playback from various [media sources](/docs/SOURCES.md)
* Notes on [developing the library itself](/docs/DEVELOPING.md)
* Rough [state diagram](/docs/state_diagram.svg) of the [Player](src/Player.js)
* View the [changelog](/CHANGELOG.md)

License
-------

All JavaScript, Android and iOS code licensed under MIT license, see LICENSE
file. Some of the files are from React Native templates and are licensed
accordingly.
