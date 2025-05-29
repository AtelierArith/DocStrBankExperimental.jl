```
fit!(stat::OnlineStat, data)
```

`stat`の「十分統計量」をより多くのデータで更新します。`typeof(data)`が提供された`stat`の単一観測の型でない場合、`fit!`は`data`内の各アイテムを反復処理し、各アイテムに対して`fit!`を試みます。したがって、`fit!(Mean(), 1:10)`は大まかに次のように翻訳されます：

```julia
o = Mean()

for x in 1:10
    fit!(o, x)
end
```
