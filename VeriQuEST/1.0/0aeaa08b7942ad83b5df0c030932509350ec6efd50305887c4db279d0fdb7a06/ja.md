```
get_verified_flow_output(T, resource, vertex)
```

与えられた頂点に対するMBQCリソース状態の検証されたフロー出力を取得します。

# 引数

  * `T`: フローのタイプで、`ForwardFlow`または`BackwardFlow`のいずれかでなければなりません。
  * `resource`: MBQCリソース状態。
  * `vertex`: 検証されたフロー出力を取得するための頂点。

# 戻り値

  * フロー出力が与えられた頂点の近傍にある有効な頂点である場合、検証されたフロー出力を返します。
  * フロー出力が`Nothing`の場合、`nothing`を返します。
  * フロータイプが`ForwardFlow`でも`BackwardFlow`でもない場合、エラーをスローします。

# 例

```julia
T = ForwardFlow()
resource = MBQCResourceState(...)
vertex = 1
output = get_verified_flow_output(T, resource, vertex) # 与えられた頂点の検証されたフロー出力を返します
```
