汎用フレームを読み取ります。すべてのフレームは以下のワイヤフォーマットを持っています：

0      1         3      7                  size+7     size+8 +–––+––––-+––––-+ +––––––-+ +–––––-+ | type | channel | size    | |    payload  | | frame-end | +–––+––––-+––––-+ +––––––-+ +–––––-+ octet    short     long       'size' octets      octet
