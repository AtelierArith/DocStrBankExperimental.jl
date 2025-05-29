```
transmissionloss(pm::PropagationModel, tx1::AcousticSource, rx1::AcousticReceiver; mode=:coherent)
transmissionloss(pm::PropagationModel, tx1::AcousticSource, rx::AbstractArray{<:AcousticReceiver}; mode=:coherent)
```

`tx1`から`rx1`、または`rx`内のすべての受信機へのdBでの伝送損失を計算します。モードは`:coherent`または`:incoherent`のいずれかです。
