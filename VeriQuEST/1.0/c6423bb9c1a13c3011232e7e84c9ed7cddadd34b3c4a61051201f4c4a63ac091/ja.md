```
get_verified_flow(T, resource::MBQCResourceState)
```

与えられた頂点の検証されたフロー出力を返す関数を作成します。

# 引数

  * `T`: フローネットワーク。
  * `resource`: MBQCリソース状態。

# 戻り値

頂点を入力として受け取り、検証されたフロー出力を返す関数 `f`。

# 例

```julia
T = ForwardFlow()
resource = MBQCResourceState(...)
f = get_verified_flow(T, resource) # 頂点を入力として受け取り、検証されたフロー出力を返す関数を返します
```
