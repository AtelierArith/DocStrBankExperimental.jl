```
finalize_lpcm_stream(stream::AbstractLPCMStream)::Bool
```

`stream`を終了し、`stream`を構築するために使用された基盤のI/Oオブジェクトがまだオープンで使用可能な場合は`true`を返します。そうでない場合は、基盤のI/Oオブジェクトが終了の結果として閉じられたことを示すために`false`を返します。
