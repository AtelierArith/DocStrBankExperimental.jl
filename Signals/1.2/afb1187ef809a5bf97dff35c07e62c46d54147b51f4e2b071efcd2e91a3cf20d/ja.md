```
 s = for_signal(f::Function, range, args...; fps = 1)
```

`f(i,args....)`を`1/fps`秒ごとに更新する`Signal`を作成します。`range`と`args`は`Signal`型または他の任意の型であることができます。ループは引数のいずれかが更新されると開始されます。前のforループが完了していない場合はキャンセルされます。

# 例

```
rng = Signal(1:5)
A = Signal(2)
B = for_signal(rng,A;fps = 30) do i,a
    println(a^i)
end;
```
