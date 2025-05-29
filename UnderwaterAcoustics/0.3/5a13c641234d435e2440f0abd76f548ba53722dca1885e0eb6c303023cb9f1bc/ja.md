```
transfercoef(pm::PropagationModel, tx1::AcousticSource, rx1::AcousticReceiver; mode=:coherent)
transfercoef(pm::PropagationModel, tx1::AcousticSource, rx::AbstractArray{<:AcousticReceiver}; mode=:coherent)
```

`tx1`から`rx1`または`rx`内のすべての受信機への複素伝達係数を計算します。モードは`:coherent`または`:incoherent`のいずれかです。
