```
..(start, stop)
start..stop
```

`Interval(start, stop)`を構築し、`start`と`stop`の間の閉区間を表します。`Interval`は抽象コレクションであり、`in`をサポートしますが、反復、インデックス付けなどはサポートしていません。

この区間には`start`と`stop`の両方の点が含まれます。`Interval`から`start`または`stop`を除外するには、`greaterthan`または`lessthan`関数を使用します。

# 例

```julia julia> 2 in 1..3 true

julia> 3 in 1..3 true

julia> 4 in 1..3 false

julia> 1 in greaterthan(1)..3 false

julia> 3 in 1..lessthan(3) false
```
