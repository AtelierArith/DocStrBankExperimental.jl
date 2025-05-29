```Julia
set_arg!(run::XRT.XRTWrap.Run, index, val)
set_arg!(run::XRT.XRTWrap.Run, index, val::XRT.AbstractBOArray)
set_arg!(run::XRT.XRTWrap.Run, index, val::XRT.XRTWrap.BO)

```

指定されたインデックスでカーネルの引数を設定します。注意してください、これはC++ APIへの薄いラッパーであるため、インデックスは0から始まります！
