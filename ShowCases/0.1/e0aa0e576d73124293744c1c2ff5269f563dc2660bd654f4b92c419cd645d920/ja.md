```
Styled{𝒯}
```

`AbstractShow` のラッパーで、表示されるときはラップされたオブジェクトとして表示されますが、`Style`（色やテキストの太さなど）を持ちます。

## コンストラクタ

  * `Styled(o, color, bold=false)`
  * `Styled(o; color=:normal, bold=false)`

## 引数

  * `o`: ラップするオブジェクト。
  * `color`: `prinstyled` に渡される色指定子、`Style` も参照してください。
  * `bold`: テキストを太字としてレンダリングするかどうか。
