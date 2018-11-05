# Parking
Shell script to install a [Parking Masternode](https://parkingcrypto.org/) on a Linux server running Ubuntu 14.04, 16.04 or 18.04. Use it on your own risk.

***
## Installation wallet (latest version):
```
wget https://raw.githubusercontent.com/parkingcrypto/Parking-MN-Install/master/install.sh 
sudo chmod 755 install.sh && ./install.sh
```
***
## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows Wallet
1. Open the Parking Desktop Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **1000** **Parking** to **MN1**.
4. Wait for 20 confirmations.
5. Go to **Tools -> "Debug console - Console"**
6. Type the following command: **masternode outputs**
7. Go to  ** Tools -> "Open Masternode Configuration File"
8. Add the following entry:
```
Alias Address Privkey TxHash Output_index
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* Output index:  **Second value from Step 6**
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is unlocked.
12. Open **Debug Console** and type:
```
startmasternode "alias" "0" "MN1"
```
***

## Usage:
```
parking-cli getinfo
parking-cli mnsync status
parking-cli masternode status
```
Also, if you want to check/start/stop **Parking** , run one of the following commands as **root**:

**Ubuntu 16.04 or 18.04**:
```
systemctl status parking #To check the service is running.
systemctl start parking #To start parking service.
systemctl stop parking #To stop parking service.
systemctl is-enabled parking #To check whetether parking service is enabled on boot or not.
```
**Ubuntu 14.04**:  
```
/etc/init.d/parking start #To start parking service
/etc/init.d/parking stop #To stop parking service
/etc/init.d/parking restart #To restart parking service
```
***
