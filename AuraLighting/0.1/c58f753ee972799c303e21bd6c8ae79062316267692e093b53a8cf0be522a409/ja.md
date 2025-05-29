```
function setcolor(au::AuraControl, rgb::Integer)
```

LEDライトの色を24ビットRGB形式の整数として設定します。色は16進数の形式0xRRGGBBで、RRは赤の成分、GGは緑、BBは24ビットRGBでコーディングされた色の青の値です。黒は0、白は0x00ffffff、赤は0xff0000、緑は0x00ff00、青は0x0000ffです。
