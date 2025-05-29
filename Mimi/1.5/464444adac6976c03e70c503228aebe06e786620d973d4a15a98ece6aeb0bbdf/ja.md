```
connect_param!(obj::AbstractCompositeComponentDef,
    dst::Pair{Symbol, Symbol}, src::Pair{Symbol, Symbol},
    backup::Union{Nothing, Array}=nothing;
    ignoreunits::Bool=false, backup_offset::Union{Nothing, Int} = nothing)
```

コンポジット `obj` のコンポーネント `dst[1]` のパラメータ `dst[2]` を、同じコンポジットの別のコンポーネント `src[1]` の変数 `src[2]` にバインドします。`backup` を使用してデフォルト値を提供し、`ignoreunits` フラグを使用して2つの間で単位の一致を確認する必要があることを示します。`backup` データが設定されている場合にのみ有効な `backup_offset` 引数は、ソースコンポーネントが開始した後の指定されたタイムステップ数に対してバックアップデータを使用する必要があることを示します。つまり、宛先コンポーネントのパラメータがソースコンポーネントのデータを2番目のタイムステップ以降のみ使用する場合、値は `1` になります。
