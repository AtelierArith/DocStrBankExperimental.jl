```
tags(x::IndexEntry)
```

チェックポイントのすべてのタグとその値。これはペアのコレクションです。たとえば、チェックポイントが次のように保存された場合：

```julia
with_tag(:sim_now=>DateTime(2000,1,1,9,00), grid=ERCOT) do
    checkpoint(Forecasters, "forecasts", ...)`
end
```

その場合、`tags(x)`は次のように返します：`(:sim_now="2000-01-01T09:00:00", :grid=>"ERCOT")`。

タグがユニークである場合、その値は`getproperty`のオーバーロードを介してもアクセスできます。たとえば、`x.sim_now`や`x.grid`としてアクセスできます。
