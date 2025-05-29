```
Scope(<キーワード引数>)
```

メッセージを送受信できるオブジェクトです。

# 引数

  * `dom`: スコープがブラウザに表示されるときにレンダリングされるDOMノード。
  * `imports`: スコープがマウントされるときにロードする`Asset`のコレクション（詳細は[`Asset`](@ref)を参照）。エントリが`Asset`でない場合は、`Asset`を構築するための引数である必要があります。

# 例

```julia
myscope = Scope(
    dom=node(:p, "私は小さなスコープです！"),
    imports=[Asset("foo.js"), "bar.css", "spam" => "spam.js"],
)
```
