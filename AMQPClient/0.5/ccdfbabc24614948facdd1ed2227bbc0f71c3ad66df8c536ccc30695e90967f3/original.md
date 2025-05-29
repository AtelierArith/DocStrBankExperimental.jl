Read a generic frame. All frames have the following wire format:

0      1         3      7                  size+7     size+8 +–––+––––-+––––-+ +––––––-+ +–––––-+ | type | channel | size    | |    payload  | | frame-end | +–––+––––-+––––-+ +––––––-+ +–––––-+ octet    short     long       'size' octets      octet
