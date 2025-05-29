```
connect_param!(m::Model, dst_comp_name::Symbol, dst_par_name::Symbol, 
                src_comp_name::Symbol, src_var_name::Symbol, 
                backup::Union{Nothing, Array}=nothing; ignoreunits::Bool=false, 
                backup_offset::Union{Int, Nothing}=nothing)
```

モデル `m` のコンポーネント `dst_comp_name` のパラメータ `dst_par_name` を、同じモデルの別のコンポーネント `src_comp_name` の変数 `src_var_name` にバインドします。`backup` を使用してデフォルト値を提供し、`ignoreunits` フラグを使用して両者の単位の一致を確認する必要があることを示します。`backup_offset` 引数は、`backup` データが設定されている場合にのみ有効で、ソースコンポーネントが開始した後の指定されたタイムステップ数に対してバックアップデータを使用することを示します。つまり、目的のコンポーネントのパラメータがソースコンポーネントのデータを2番目のタイムステップ以降のみ使用する場合、値は `1` になります。
