```
mukai_lattice(S::Symbol = :K3; extended::Bool = false)
```

(拡張された) ムカイ格子を返します。

`S == :K3` の場合、K3曲面上の安定シーブのモジュライ空間に変形同値なハイパーカーレマン多様体に関連する (拡張された) ムカイ格子を返します。

`S == :Ab` の場合、アーベル多様体上の安定シーブのモジュライ空間に変形同値なハイパーカーレマン多様体に関連する (拡張された) ムカイ格子を返します。

# 例

```jldoctest
julia> L = mukai_lattice();

julia> genus(L)
整数格子のための属記号
署名: (4, 0, 20)
局所記号:
  2における局所属記号: 1^24

julia> L = mukai_lattice(; extended = true);

julia> genus(L)
整数格子のための属記号
署名: (5, 0, 21)
局所記号:
  2における局所属記号: 1^26

julia> L = mukai_lattice(:Ab);

julia> genus(L)
整数格子のための属記号
署名: (4, 0, 4)
局所記号:
  2における局所属記号: 1^8

julia> L = mukai_lattice(:Ab; extended = true);

julia> genus(L)
整数格子のための属記号
署名: (5, 0, 5)
局所記号:
  2における局所属記号: 1^10
```
