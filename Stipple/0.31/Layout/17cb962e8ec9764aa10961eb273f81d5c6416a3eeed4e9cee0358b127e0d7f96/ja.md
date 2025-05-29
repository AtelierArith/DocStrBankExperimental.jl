```
add_css(css::Function; update = true)
```

`THEMES[]`にcss関数を追加します。

### パラメータ

  * `css::Function` - スタイル要素のベクトルを生成する関数
  * `update` - 同じ名前の既存のスタイルシートを削除するかどうかを決定します

### 例

```julia
# q-table行のストリプルコアカラー形式を削除するためのcss
# （これにより、属性 `table-class` によるフォントカラー設定が有効になります）

function mycss()
  [
    style("""
    .stipple-core .q-table tbody tr { color: inherit; }
    """)
  ]
end

add_css(mycss)
```
