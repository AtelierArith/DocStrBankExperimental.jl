```
generateclassdata(c[, shuffle])
```

`ClassData` 構造体を入力として与えると、3つのクラスのデータを生成します。3つのクラスの信号を含む行列と、それに対応するラベルを含むベクトルを返します。

N. Saito と R. Coifman による "Local Discriminant Basis and their Applications" の Journal of Mathematical Imaging and Vision, Vol. 5, 337-358 (1995) に基づいています。

# 引数

  * `c::ClassData`: 生成する信号クラスのタイプ。
  * `shuffle::Bool`: (デフォルト: `true`) 信号をシャッフルするかどうか。

# 戻り値

  * `::Matrix{Float64}`: 生成された信号。
  * `::Vector{Int64}`: 生成された信号の各列に対応するクラス。

# 例

```@repl
using WaveletsExt

c = ClassData(:tri, 100, 100, 100)
generateclassdata(c)
```

**関連情報:** [`ClassData`](@ref)
