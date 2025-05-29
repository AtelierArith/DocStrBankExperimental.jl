```
new_derived_named_parameter(variable, value, extra::String; kw...)
```

もし `value isa Num` であれば `value` を返します。もし `value isa LiteralParameter` であれば、そのリテラル値に置き換えます。それ以外の場合は、`variable` から作成された新しい MTK `@parameter` を作成します（`variable` は単なる `Symbol` である可能性もあります） `extra` 文字列を追加します。

**キーワード**:

  * `prefix = true`: `extra` が先頭または末尾に追加されるかどうか、`connector` で接続します。
  * `connector = "_"`: `extra` と名前を接続するために使用するもの。

例えば、

```
@variables x(t)
p = new_derived_named_parameter(x, 0.5, "τ")
```

今 `p` は名前 `:τ_x` とデフォルト値 `0.5` を持つパラメータになります。
