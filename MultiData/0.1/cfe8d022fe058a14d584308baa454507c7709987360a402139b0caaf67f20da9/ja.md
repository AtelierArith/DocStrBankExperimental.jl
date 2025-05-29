```
variables(md, i)
```

マルチモーダルデータセット内の変数の名前を `Symbol` として返します。

`MultiDataset` 型のオブジェクトに対して呼び出されると、モダリティインデックスを `AbstractVector{Symbol}` にマッピングする `Dict` が返されます。

注意: 変数名の順序は、モダリティ内の変数の順序と一致することが保証されています。

もしインデックス `i` が第二引数として渡されると、`i` 番目のモダリティの変数名が `AbstractVector` として返されます。

あるいは、単一のモダリティに対して `nvariables` を呼び出すこともできます。

# 引数

  * `md` は MultiDataset です;
  * `i` はマルチモーダルデータセットから変数名を取得するモダリティを示す `Integer` です。

# 例

```julia-repl
julia> md = MultiDataset([[2],[3]], DataFrame(:name => ["Python", "Julia"], :age => [25, 26], :sex => ['M', 'F']))
● MultiDataset
   └─ 次元数: (0, 0)
- モダリティ 1 / 2
   └─ 次元数: 0
2×1 SubDataFrame
 Row │ age
     │ Int64
─────┼───────
   1 │    25
   2 │    26
- モダリティ 2 / 2
   └─ 次元数: 0
2×1 SubDataFrame
 Row │ sex
     │ Char
─────┼──────
   1 │ M
   2 │ F
- 予備変数
   └─ 次元数: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia

julia> variables(md)
Dict{Integer, AbstractVector{Symbol}} with 2 entries:
  2 => [:sex]
  1 => [:age]

julia> variables(md, 2)
1-element Vector{Symbol}:
 :sex

julia> variables(md, 1)
1-element Vector{Symbol}:
 :age

julia> mod2 = modality(md, 2)
2×1 SubDataFrame
 Row │ sex
     │ Char
─────┼──────
   1 │ M
   2 │ F

julia> variables(mod2)
1-element Vector{Symbol}:
 :sex
```
