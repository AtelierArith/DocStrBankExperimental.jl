```
@promise_no_assign expr
```

`expr`を評価しますが、`BaseDirs`の結果がグローバル定数に割り当てられないことを約束します。

このマクロは、他のパッケージのプリコンパイルスクリプトで使用することを意図しており、グローバル定数の割り当てに関する不必要な警告を抑制します。プリコンパイルの外で使用されると、自身が警告を出します。

# 例

プリコンパイル作業内で：

```julia
BaseDirs.@promise_no_assign MyPkg.somecall()
```

または、`begin ... end`を使ってより大きなブロックを安全としてマークすることもできます：

```julia
BaseDirs.@promise_no_assign begin
    ...
    MyPkg.somecall()
    ...
end
```
