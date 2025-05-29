```
restoreoptsum!(m::MixedModel, io::IO; atol::Real=0, rtol::Real=atol>0 ? 0 : √eps)
restoreoptsum!(m::MixedModel, filename; atol::Real=0, rtol::Real=atol>0 ? 0 : √eps)
```

JSONストリームまたはファイル名から`optsum`フィールドを読み取り、チェックし、復元します。
