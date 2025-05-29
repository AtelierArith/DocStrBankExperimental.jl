```
check_names(checkset::CheckSet)::Vector{String}
```

指定されたチェックセット内のすべてのチェックの名前を取得します。

# 引数

  * `checkset::CheckSet`: チェックセットオブジェクト。

# 戻り値

指定されたチェックセット内のチェック名のベクター。

# 例

```julia
names = check_names(checkset)  # Returns ["check1", "check2", ...]
```
