```
async_latest(observable::AbstractObservable, n=1)
```

`observable`への更新が更新間の間隔よりも長くかかる場合、`observable`への最後の`n`回の更新以外をすべてドロップする`Observable`を返します。

これは、スライダーから計算に時間がかかるプロット関数に更新を渡したい場合に便利です。プロットは、中間のものをスキップして最後のフレームを直接計算します。

# 例:

```
observable = Observable(0)
function compute_something(x)
    for i=1:10^8 rand() end # 高コストな処理をシミュレート
    println("updated with $x")
end
o_latest = async_latest(observable, 1)
on(compute_something, o_latest) # 最新の更新で何かを計算

for i=1:5
    observable[] = i
end
```
