# The Guardian: Advanced Network Filtering

**The Guardian** is a Content Blocker for Chrome and Edge browsers. Future versions will be available for Firefox and Safari.

The Guardian can work standalone, with the features of a powerful Content Blocker, or, by installing **Advanced Network Filtering** (**ANF**), with the ability to filter network traffic and control exactly which domains and IP addresses are to be blocked.

But there's more. By installing and enabling ANF using The Guardian, network filtering will be global to the device where ANF is installed and therefore extended to all installed applications, not just browsers.

To define which domains and IP addresses should be blocked, ANF uses a simple text file with a list of domains to block.

The Guardian extension has the ability to control ANF by sending it one of the commands predefined during the design phase. 
Currently, The Guardian offers the ability to enable, disable, and request the status of ANF using a section of its Popup. In future versions of The Guardian, other commands will be added, such as the ability to add/remove personal domains in the ANF blacklist.

The Guardian uses the **NativeMessaging** API to interface with ANF, interfacing with a custom **NativeMessagingHost** created ad hoc. The NativeMessagingHost sends commands to and receives responses from ANF.

ANF is structurally composed of two Windows services, **GuardianMITM**, which interfaces with The Guardian (or rather, with its NativeMessagingHost), and **[DNSCrypt-Proxy](https://github.com/DNSCrypt/dnscrypt-proxy)**, which acts as a filter over the network and increases security. For more details on all the features of DNSCrypt, please refer to its excellent documentation.

**GuardianMITM**, the *Man-In-The-Middle*, is capable of distributing requests and responses to and from The Guardian and DNSCrypt, as well as managing the configuration and restoration of network interfaces when DNSCrypt is enabled or disabled in a completely transparent way. This means that **the user does not have to manually configure** any interface to work with a protected network nor manually restore interfaces to their original settings when DNSCrypt is disabled.

Currently, ANF can only be manipulated using The Guardian. The next version, while remaining fully compatible with The Guardian, will also have a graphical interface, where the user will be able to perform various operations, such as defining which physical interface to apply ANF to (all active ones, only WiFi, only an Ethernet card, etc.), manipulating the blacklist in a real editor, etc., transforming ANF into a standalone too product.
