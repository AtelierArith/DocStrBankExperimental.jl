```
Spectrum!(spec::AbstractVector{Tv}, vec::AbstractVector{Tv}, size::Ti) where {Tv<:Complex, Ti<:Integer}
```

ユーザーが提供したベクトルからスペクトルを設定します。実際、この関数は与えられたスペクトルベクトルのサイズが十分であるかどうかを確認するだけです。そして、`vec`の最初の`size`要素を`spec`にコピーします。
