# _冷衫之眼_说明

冷衫之眼 协议是电脑（智能手机/平板电脑）和微控制器进行通信的协议, 可以直接在电脑上控制IO, 通过在串口发送两个字节的数据,让IO口或者I2C等IO端口高低电平变化. 


## 两种使用方式

###　第一种是把 冷衫之眼 运行在Arduino设备上, 
  
  * 数字量使用  ``` Firmata.sendAnalog(analogPin, analogRead(analogPin)) ``` 
  * 发送字符串  ``` Firmata.sendString(stringToSend) ```. 
  * 在Arduino中: See File -> Examples -> Firmata -> AnalogFirmata 或者 EchoString dier
  
### 第二种是 在 Arduino上的协议实现,然后通过串口、蓝牙、wifi、网口和上位机进行通信. File -> Examples -> Firmata
  
   * StandardFirmata 标准实现
   * StandardFirmataPlus ICBrickCore的标准实现
   * StandardFirmataEthernet (以太网)
   * StandardFirmataBLE 蓝牙4.0



## 使用Arduino1.6.9 --在线安装

1. Open the Arduino IDE and navigate to: `Sketch > Include Library > Manage Libraries`
2. Filter by "Firmata" and click on the "Firmata by Firmata Developers" item in the list of results.
3. Click the `Select version` dropdown and select the most recent version (note you can also install previous versions)
4. Click `Install`.
5. 打开 StandardFirmataPlus,上传



### 复制库的安装方式(不推荐)

If you are contributing to Firmata or otherwise need a version newer than the latest tagged release, you can clone Firmata directly to your Arduino/libraries/ directory (where 3rd party libraries are installed). This only works for Arduino 1.6.4 and higher, for older versions you need to clone into the Arduino application directory (see section below titled "Using the Source code rather than release archive"). Be sure to change the name to Firmata as follows:

```bash
$ git clone git@github.com:firmata/arduino.git ~/Documents/Arduino/libraries/Firmata
```

*Update path above if you're using Windows or Linux or changed the default Arduino directory on OS X*

## 其他

 * 聊天室 [![Gitter](https://badges.gitter.im/Join Chat.svg)](https://gitter.im/firmata/arduino?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
 * [冷衫芝客户端](客户端.md)
 * 

##Updating Firmata in the Arduino IDE - older versions (<= 1.6.3 or 1.0.x)   不再支持 

###Mac OSX:

The Firmata library is contained within the Arduino package.

1. Navigate to the Arduino application
2. Right click on the application icon and select `Show Package Contents`
3. Navigate to: `/Contents/Resources/Java/libraries/` and replace the existing
`Firmata` folder with latest [Firmata release](https://github.com/firmata/arduino/releases/tag/2.5.2) (note there is a different download
for Arduino 1.0.x vs 1.6.x)
4. Restart the Arduino application and the latest version of Firmata will be available.

*If you are using the Java 7 version of Arduino 1.5.7 or higher, the file path
will differ slightly: `Contents/Java/libraries/Firmata` (no Resources directory).*

###Windows:

1. Navigate to `c:/Program\ Files/arduino-1.x/libraries/` and replace the existing
`Firmata` folder with the latest [Firmata release](https://github.com/firmata/arduino/releases/tag/2.5.2) (note there is a different download
for Arduino 1.0.x vs 1.6.x).
2. Restart the Arduino application and the latest version of Firmata will be available.

*Update the path and Arduino version as necessary*

###Linux:

1. Navigate to `~/arduino-1.x/libraries/` and replace the existing
`Firmata` folder with the latest [Firmata release](https://github.com/firmata/arduino/releases/tag/2.5.2) (note there is a different download
for Arduino 1.0.x vs 1.6.x).
2. Restart the Arduino application and the latest version of Firmata will be available.

*Update the path and Arduino version as necessary*

###Using the Source code rather than release archive (only for versions older than Arduino 1.6.3)

*It is recommended you update to Arduino 1.6.4 or higher if possible, that way you can clone directly into the external Arduino/libraries/ directory which persists between Arduino application updates. Otherwise you will need to move your clone each time you update to a newer version of the Arduino IDE.*

If you're stuck with an older version of the IDE, then follow these keep reading otherwise jump up to the "Cloning Firmata section above".

Clone this repo directly into the core Arduino application libraries directory. If you are using
Arduino 1.5.x or <= 1.6.3, the repo directory structure will not match the Arduino
library format, however it should still compile as long as you are using Arduino 1.5.7
or higher.

You will first need to remove the existing Firmata library, then clone firmata/arduino
into an empty Firmata directory:

```bash
$ rm -r /Applications/Arduino.app/Contents/Resources/Java/libraries/Firmata
$ git clone git@github.com:firmata/arduino.git /Applications/Arduino.app/Contents/Resources/Java/libraries/Firmata
```

*Update paths if you're using Windows or Linux*

To generate properly formatted versions of Firmata (for Arduino 1.0.x and Arduino 1.6.x), run the
`release.sh` script.


<a name="contributing" />
##Contributing

If you discover a bug or would like to propose a new feature, please open a new [issue](https://github.com/firmata/arduino/issues?sort=created&state=open). Due to the limited memory of standard Arduino boards we cannot add every requested feature to StandardFirmata. Requests to add new features to StandardFirmata will be evaluated by the Firmata developers. However it is still possible to add new features to other Firmata implementations (Firmata is a protocol whereas StandardFirmata is just one of many possible implementations).

To contribute, fork this repository and create a new topic branch for the bug, feature or other existing issue you are addressing. Submit the pull request against the *master* branch.

If you would like to contribute but don't have a specific bugfix or new feature to contribute, you can take on an existing issue, see issues labeled "pull-request-encouraged". Add a comment to the issue to express your intent to begin work and/or to get any additional information about the issue.

You must thoroughly test your contributed code. In your pull request, describe tests performed to ensure that no existing code is broken and that any changes maintain backwards compatibility with the existing api. Test on multiple Arduino board variants if possible. We hope to enable some form of automated (or at least semi-automated) testing in the future, but for now any tests will need to be executed manually by the contributor and reviewers.

Use [Artistic Style](http://astyle.sourceforge.net/) (astyle) to format your code. Set the following rules for the astyle formatter:

```
style = ""
indent-spaces = 2
indent-classes = true
indent-switches = true
indent-cases = true
indent-col1-comments = true
pad-oper = true
pad-header = true
keep-one-line-statements = true
```

If you happen to use Sublime Text, [this astyle plugin](https://github.com/timonwong/SublimeAStyleFormatter) is helpful. Set the above rules in the user settings file.
