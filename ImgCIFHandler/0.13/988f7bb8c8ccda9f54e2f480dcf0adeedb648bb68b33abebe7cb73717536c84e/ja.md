```
get_detector_axis_settings(imgcif,scanid,frameno)
```

指定されたフレームのすべての検出器軸の設定を、軸名、タイプ、設定の順に返します。値は、*_diffrn*scan*axis*情報から計算されますが、*_diffrn*scan*frame*axis*が欠落している場合は計算されます。ファイルに明示的に定義されたスキャンがない場合は、`scanid`を`nothing`または`missing`に設定してください。
