```
Status(vars)
```

シミュレーション中に変数の値を格納するために使用されるStatus型です。主に、`TimeStepTable`の`TimeStepRow`に変数を格納するための構造体として使用されます（[`PlantMeteo.jl`のドキュメント](https://palmstudio.github.io/PlantMeteo.jl/stable/)を参照）。[`ModelList`](@ref)の一部です。

ほとんどのコードはMasonProtter/MutableNamedTuples.jlから取られているため、`Status`はMutableNamedTuplesのいくつかの修正を加えたものであり、本質的には変数の値への参照の`NamedTuple`を格納する構造体であり、これにより可変になります。

# 例

すべての変数に対して1つの値を持つ葉は、1つのタイムステップを持つステータスを作成します：

```jldoctest st1
julia> using PlantSimEngine
```

```jldoctest st1
julia> st = PlantSimEngine.Status(Rₛ=13.747, sky_fraction=1.0, d=0.03, aPPFD=1500.0);
```

これらのインデックス方法はすべて有効です：

```jldoctest st1
julia> st[:Rₛ]
13.747
```

```jldoctest st1
julia> st.Rₛ
13.747
```

```jldoctest st1
julia> st[1]
13.747
```

Status変数を設定するのは非常に簡単です：

```jldoctest st1
julia> st[:Rₛ] = 20.0
20.0
```

```jldoctest st1
julia> st.Rₛ = 21.0
21.0
```

```jldoctest st1
julia> st[1] = 22.0
22.0
```
