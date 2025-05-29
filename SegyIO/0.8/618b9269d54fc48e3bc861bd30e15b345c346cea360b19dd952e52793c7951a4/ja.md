```
split(s::SeisBlock, inds::Union{Vector{Ti}, AbstractRange{Ti}};
           consume::Bool = false) where {Ti<:Integer}
```

`s`の'ind'トレースを別の`SeisBlock`オブジェクトに分割します。

デフォルトの動作では、入力オブジェクト`s`は変更されません。返される`SeisBlock`は、`s`のトレースヘッダーを参照して作成され、データのサブセットをコピーします。

メモリ使用量が懸念される場合、`consume`キーワードは`merge`の動作を変更します。`consume`がtrueの場合、`s`の'ind'トレースは削除され、返される`SeisBlock`オブジェクトに配置されます。この場合、`merge`は`s`に対してインプレースで操作を行いながら、`s`のサブセットを返します。

# 例

```
julia> using SegyIO

julia> s = segy_scan(joinpath(dirname(pathof(SegyIO)),"data/"), "overthrust", ["GroupX"; "GroupY"], verbosity = 0);

julia> d = s[1:length(s)]; @time b = split(d, 1:10000);
  0.005683 seconds (23 allocations: 28.649 MiB, 17.99% gc time)

julia> println("d: ", size(d)); println("b: ", size(b))
d: (751, 20013)
b: (751, 10000)

julia> data_in_memory = Base.summarysize(d.data) + Base.summarysize(b.data)
90159052
```

`merge`のデフォルトの動作は、`d`をコピーして`b`を作成することに注意してください。

```
julia> d = s[1:length(s)]; @time b = split(d, 1:10000, consume=true);
  0.062364 seconds (37 allocations: 116.537 MiB, 19.44% gc time)

julia> println("d: ", size(d)); println("b: ", size(b))
d: (751, 10013)
b: (751, 10000)

julia> data_in_memory = Base.summarysize(d.data) + Base.summarysize(b.data)
60119052
```

この場合、`consume`がtrueに設定されていたため、`merge`は`d`からトレースを削除して`b`を作成しました。`consume`は、パフォーマンス、メモリ割り当て、リスクのコストをかけてメモリ内のデータの重複を防ぎます。
