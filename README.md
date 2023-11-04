### - Note: Welcome to try out it, You Agree to Proceed and Use at your own risk. **
- [Releases](https://github.com/MrTaiKe/Action_OpenWrt_Xiaomi_R4AGv2/releases)

```
openwrt-ramips-mt7621-xiaomi_mi-router-4a-gigabit-v2-squashfs-sysupgrade.bin

By the way, the password is password
```

### There are two types of firmware [releases](https://github.com/MrTaiKe/Action_OpenWrt_Xiaomi_R4AGv2/releases)
    1. CSW-LEDE-R22.10.1 Kernel 5.4.214 (use coolsnowwolf/lede R22.10.1)
    2. Openwrt-v22.03.2 Kernel_5.10.146 (use openwrt stable releases v22.03.2)
### Projects divided into two seperate folders:
    1. LEDE
    2. opwrt-22.03.2
    
![image](https://user-images.githubusercontent.com/117250841/200182184-1374ebfe-cca5-40fb-a7ca-4eaa1444f2f0.png)

### - Note: LED lights NOT working properly.
### - Packages added:
  - https://github.com/kenzok8/small-package
  - https://github.com/jerrykuku/luci-theme-argon.git

## How to built/Compile Openwrt firmware(bin)?
If you want to learn about it, you can visit the followings:
  - https://github.com/wbs306/Action_OpenWrt_Xiaomi_R4AG, Xiaomi R4A Gigabit Breed Flash (NOT for R4AGv2)
  - https://github.com/wbs306/lede
  
### Thanks to [wbs306](https://github.com/wbs306)

- Many Thanks to wbs306's codes for Xiaomi R4AG V2 hardware changes! [wbs306/lede@a2a3a4a](https://github.com/coolsnowwolf/lede/commit/a2a3a4a8d2b4c427e066200a8a64289fe4d6c281) 

    1. target/linux/ramips/dts/mt7621_xiaomi_mi-router-4a-gigabit-v2.dts
    2. target/linux/ramips/image/mt7621.mk
    3. target/linux/ramips/mt7621/base-files/etc/board.d/02_network

## How to BREED flash Openwrt bin file?

###  Step#1 How to Telnet(talk) to R4AGv2 Router? 

Successfully used @LordPinhead's code [commit #99634522](https://github.com/acecilia/OpenWRTInvasion/pull/155/commits/996345221db8800a569093fd7ad5a642b160bcbc) to telnet XiaoMi R4A V2 Gigabit (RA4Gv2) 

```
#Run the script
    pip3 install -r requirements.txt # Install requirements 
    python3 remote_command_execution_vulnerability_v2.py
```

###  Step#2 How to install bootloader "BREED" onto R4AGv2 router?
```
    1. Refer to this instrution https://www.right.com.cn/forum/thread-4007071-1-1.html
    (This instruction is just a reference, make your own judgements and adjustments to what you need)
    
    2. Go to https://breed.hackpascal.net, For RA4Gv2, download breed-mt7621-pbr-m1.bin 
    After successfully Telnet 192.168.31.1, use ftp app, copy it over to router's tmp folder.
    
    3. run the following script
    mtd -r write /tmp/breed-mt7621-pbr-m1.bin Bootloader
```

![image](https://user-images.githubusercontent.com/117250841/200181357-1ba254f4-51ad-4442-974e-de9b38519f25.jpeg)

###  Step#3 How to Use BREED web to flash Openwrt Firmware(bin) onto R4AGv2 router?

```
1. Connect Ethernet Cable to LAN port rather than WAN port.
2. Hold & press reset, power on
3. Open browser, go to 192.168.1.1 for Breed Web Page
4. Flash these two bin files together at the same time! 
    - eeprom.bin
    - openwrt-ramips-mt7621-xiaomi_mi-router-4a-gigabit-v2-squashfs-sysupgrade.bin
```
![image](https://user-images.githubusercontent.com/117250841/200181428-b9628072-b1d6-4f23-a799-3b06c63c12bb.png)
![image](https://user-images.githubusercontent.com/117250841/200880220-1ed7a02a-c35b-4cd6-ba71-a6c85778a572.jpeg)

```
1. Connect Ethernet Cable to LAN port rather than WAN port
2. PLEASE NOTE: router IP might be changed to 192.168.31.1
3. If Router doesn't have DHCP enabled, you will need to manually assign IP to talk to your router:
For example:
    If router's IP is 192.168.1.2
    Manually assign your computer's ip to be: 
    192.168.1.88
    255.255.255.0
    
    Default wifi SSID: WiFi_R4AGv2
    Defulat wifi Key: password
```

