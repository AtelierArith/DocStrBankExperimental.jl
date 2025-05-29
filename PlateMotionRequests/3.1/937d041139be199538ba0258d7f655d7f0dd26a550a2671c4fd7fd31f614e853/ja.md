```
platemotion(lats, lons, heights; kwargs...)
platemotion(lats, lons; kwargs...)
```

[UNAVCO Plate Motion Calculator][1]からプレート運動データをリクエストします。出力からヘッダーとメタデータが削除され、[`Table`][2]に解析されます。緯度、経度、オプションで高さのための別々のベクトルを受け入れます。

関連情報: [`write_platemotion`](@ref)。

!!! note
    サイト名はサポートされていません。'ansii'、'ansii_xyz'、および 'psvelo' フォーマットのみがサポートされています。すべてのオプション引数の組み合わせが許可されているわけではありません。詳細については、上記のリンク先のウェブサイトを参照してください。


オプション引数:

  * `model`: 計算に使用するプレート運動モデル、またはデフォルトでGSRM v2.1。
  * `plate`: 属性された運動のテクトニックプレート、またはデフォルトで自動プレート選択。
  * `reference`: 固定参照プレート、またはデフォルトでNNR（No Net Rotation）。
  * `up_lat`: オイラー極のカスタム座標（属性された運動）を小数度で。
  * `up_lon`: 上記を参照。
  * `up_w`: オイラー極のカスタム回転率（属性された運動）を百万年あたりの度で。
  * `up_x`: オイラー極のカスタム成分（属性された運動）を百万年あたりの度で。
  * `up_y`: 上記を参照。
  * `up_z`: 上記を参照。
  * `ur_lat`: オイラー極のカスタム座標（参照速度）を小数度で。
  * `ur_lon`: 上記を参照。
  * `ur_w`: オイラー極のカスタム回転率（参照速度）を百万年あたりの度で。
  * `ur_x`: オイラー極のカスタム成分（参照速度）を百万年あたりの度で。
  * `ur_y`: 上記を参照。
  * `ur_z`: 上記を参照。
  * `format`: 応答のデータセクションの出力フォーマット、またはデフォルトでASCII。

[1]: https://www.unavco.org/software/geodetic-utilities/plate-motion-calculator/plate-motion-calculator.html. [2]: https://typedtables.juliadata.org/latest/man/table/
