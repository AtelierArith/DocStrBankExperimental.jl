```
get_input_value(resource::MBQCResourceState, iter)
```

指定された `MBQCResourceState` から `iter` 番目のインデックスの入力値を返します。`iter` が入力インデックスの長さを超える場合、関数は `nothing` を返します。

# 引数

  * `resource`: 入力値を抽出するための `MBQCResourceState`。
  * `iter`: 入力値を抽出するインデックス。

# 例

```julia
value = get_input_value(resource, 1) # リソースの最初のインデックスの入力値を返します
```
