```
fit_spectrum(unk::Spectrum{T}, drefs::DirectReferences)::DirectFitResult{T} where { T <: Real }
```

未知のスペクトルに直接参照をフィットし、フィットからのk比率やその他の出力量を含む`DirectFitResult`構造体を返します。

驚くべきことに、この関数は`unk[:Composition]`が、`unk`が収集された材料の組成の推定を持つ`Material`として定義されていることを要求します。この情報は、連続背景をモデル化するために必要です。はい、これは循環的に思えます（そして実際にそうです）。1つのオプションは、最初にフィルターフィットを実行し、フィルターフィットを定量化し、次にこれを推定値として使用することです。
