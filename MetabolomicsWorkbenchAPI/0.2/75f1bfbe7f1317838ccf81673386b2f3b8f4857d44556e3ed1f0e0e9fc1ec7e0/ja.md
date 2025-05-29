```
check_mw(url::AbstractString) => String
```

メタボロミクスワークベンチサーバーが正しく応答しているかを確認します。HTTPステータスコードを返します（成功した場合は`200`）し、メッセージを表示します。

# 例

```julia
julia> check_mw()
MetabolomicsWorkbench.orgは生きています。
200
```
