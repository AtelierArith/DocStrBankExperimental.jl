```
get_beam_centre(incif::CifContainer,scan_id,frame_no)
```

`scan_id`の`frame_no`のビーム中心座標を返します。すべての軸位置を考慮します。ピクセル座標のスロー、ファスト、およびmm座標のスロー、ファストとして4つの値を返します。mm座標は、検出器座標の原点ではなく、原点ピクセルの中心からのものです。
