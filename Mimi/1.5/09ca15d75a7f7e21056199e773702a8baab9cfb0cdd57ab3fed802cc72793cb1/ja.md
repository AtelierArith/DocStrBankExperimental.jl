```
connect_param!(m::Model, dst::Pair{Symbol, Symbol}, src::Pair{Symbol, Symbol}, backup::Array; ignoreunits::Bool=false)
```

モデル `m` のコンポーネント `dst[1]` のパラメータ `dst[2]` を、同じモデルの別のコンポーネント `src[1]` の変数 `src[2]` にバインドします。`backup` を使用してデフォルト値を提供し、`ignoreunits` フラグを使用して両者の単位の一致を確認する必要があることを示します。`backup_offset` 引数は、`backup` データが設定されている場合にのみ有効で、バックアップデータがソースコンポーネントが開始した後の指定されたタイムステップ数に使用されることを示します。つまり、値は `1` であれば、宛先コンポーネントのパラメータはソースコンポーネントのデータを2番目のタイムステップ以降のみ使用することになります。
