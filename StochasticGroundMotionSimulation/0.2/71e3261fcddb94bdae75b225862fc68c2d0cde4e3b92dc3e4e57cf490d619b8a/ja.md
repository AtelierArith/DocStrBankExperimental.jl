```
fourier_source_shape(f::T, m::S, src::SourceParameters) where {S<:Real,T<:Float64}
```

*変位*のフーリエ振幅スペクトルのソース形状で、定数項や地震モーメントは含まれていません。これは単にソーススペクトル形状を含みます。

ソーススペクトル形状の性質は`src.model`に依存します：

  * `:Brune`は単一コーナーオメガ二乗スペクトルを提供します（これがデフォルトです）
  * `:Atkinson_Silva_2000`はAtkinson & Silva (2000)の二重コーナースペクトルを提供します
  * `:Beresnev_2019`はBeresnev (2019)の`src.n`に関連する任意の減衰率を持つ単一コーナースペクトルを提供します
