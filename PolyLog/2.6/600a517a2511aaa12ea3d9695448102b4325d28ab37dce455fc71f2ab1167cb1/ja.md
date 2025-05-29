```
reli3(x::Real)
```

実数 $x$ の実数トリロガリズム $\Re[\operatorname{Li}_3(x)]$ を返します。`Real` 型の数値です。

`Float16`、`Float32`、または `Float64` 型の $x$ に対する実装は [[arXiv:2308.11619](https://arxiv.org/abs/2308.11619)] の適応です。

著者: アレクサンダー・フォイヒト

ライセンス: MIT

# 例

```jldoctest; setup = :(using PolyLog)
julia> reli3(1.0)
1.2020569031595942
```
