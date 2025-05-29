```
@showprogress [desc="計算中..."] for i = 1:50
    # 計算はここに入ります
end

@showprogress [desc="計算中..."] pmap(x->x^2, 1:50)
```

は計算の進行状況を表示します。計算の内容やその他のオプションを指定するカスタムメッセージを任意で提供できます。

`@showprogress` はループ、内包表記、および `map`-のような関数で機能します。これらの `map`-のような関数は `ncalls` が定義されていることに依存し、`methods(ProgressMeter.ncalls)` で確認できます。新しいものは `ProgressMeter.ncalls(::typeof(mapfun), args...) = ...` を定義することで追加できます。

`@showprogress` はスレッドセーフであり、`@distributed` ループや `pmap` や `asyncmap` のようなスレッド化または分散関数でも機能します。
