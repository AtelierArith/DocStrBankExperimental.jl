```
Line(args...)
```

与えられた引数でラインプロットを表します。

# キーワード引数

## 必須

  * `x`: x座標として使用される列。デフォルト: `0`
  * `y`: y座標として使用される列。デフォルト: `0`

## ラインオプション

  * `breaks`: 欠損値が見つかったときにラインにブレークを引き起こします。デフォルト: `false`
  * `interpolate`: ラインを描画するために使用する補間関数、例: `:linear`, `:basis`, `:natural`, `:step`, ... デフォルト: `:linear`

## グルーピング

  * `group`: 観測をグループ化するための列の名前。各観測のグループは別々のラインを作成します。

## ラインの外観

  * `color`: マークのデフォルトの色。ユーザーは色の名前をシンボル（例: `:red`）、文字列（例: `"red"`）、HTMLカラー値（例: `"#4682b4"`）、または`gradient()`関数を使用してグラデーションカラーを渡すことができます。デフォルト: `"#4682b4"`
  * `dash`: ラインのダッシュスタイル。デフォルト: `[0]`
  * `opacity`: マークの不透明度。0（透明）から1（不透明）まで。デフォルト: `1`
  * `thickness`: ラインの太さ。デフォルト: `1`

## 軸オプション

  * `x2axis`: `true`に設定すると、現在のプロットに上部のx軸が使用されます。デフォルト: `false`
  * `xshift`: x方向にマークをシフトします。離散型軸に便利です。デフォルト: `0`
  * `y2axis`: `true`に設定すると、現在のプロットに右側のy軸が使用されます。デフォルト: `false`
  * `yshift`: y方向にマークをシフトします。離散型軸に便利です。デフォルト: `0`

## 凡例

  * `legend`: ユーザーはこのキーワード引数にシンボルを渡して、対応するマークの凡例のためにさらにカスタマイズが渡されることを示すことができます。ユーザーは`Legend`グローバルキーワードを介して追加のカスタマイズを提供する必要があります。

## その他

  * `clip`: マークがクリップされるべきかどうかを示します。
