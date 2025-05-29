```
dcc_geolocation(;kwargs...)
```

ジオロケーションコンポーネント CurrentLocation コンポーネントは、ウェブブラウザからデバイスのジオロケーションを取得します。詳細については、こちらを参照してください: https://developer.mozilla.org/en-US/docs/Web/API/Geolocation_API

  * `id` (String; optional): Dash コールバックでこのコンポーネントを識別するために使用される ID。
  * `high_accuracy` (Bool; optional): true の場合、デバイスがより正確な位置を提供できる場合は、そうします。

これにより、応答時間が遅くなったり、電力消費が増加する可能性があります（例えば、モバイルデバイスの GPS チップを使用している場合）。false（デフォルト値）の場合、デバイスはリソースを節約し、より迅速に応答したり、消費電力を減らすことができます。

  * `local_date` (String; optional): デバイスの位置が更新されたときのローカルの日付と時刻。

フォーマット:  MM/DD/YYYY, hh:mm:ss p   ここで p は AM または PM

  * `maximum_age` (optional): 返すことが許可される可能性のあるキャッシュされた位置の最大年齢（ミリ秒単位）。0 に設定すると、

デバイスはキャッシュされた位置を使用できず、実際の現在の位置を取得しようとしなければなりません。Infinity に設定すると、デバイスは年齢に関係なくキャッシュされた位置を返さなければなりません。デフォルト: 0。

  * `position` (要素 lat, lon, accuracy, alt, alt*accuracy, heading, speed を含むリスト   - `lat` (optional)   - `lon` (optional)   - `accuracy` (optional)   - `alt` (optional)   - `alt*accuracy`(optional)   -`heading`(optional)   -`speed`(optional); optional): デバイスの位置。`lat`、`lon`、および`accuracy` は常に返されます。その他のデータは

利用可能な場合に含まれ、それ以外の場合は NaN になります。

```
  `lat` は度単位の緯度です。
  `lon` は度単位の経度です。
  `accuracy` はメートル単位の lat/lon の精度です。    *

  `alt` は平均海面上の高度（メートル単位）です。
  `alt_accuracy` は高度の精度（メートル単位）です。
  `heading` は度単位のコンパスの見出しです。
  `speed` はメートル毎秒の速度です。
```

  * `position_error` (要素 code, message を含むリスト   - `code` (optional)   - `message` (String; optional); optional): 位置エラー
  * `show_alert` (Bool; optional): true の場合、エラーメッセージがアラートとして表示されます
  * `timeout` (optional): デバイスが位置を返すために許可される最大時間（ミリ秒単位）。

デフォルト値は Infinity で、位置が利用可能になるまでデータは返されません。

  * `timestamp` (optional): 位置が更新されたときの Unix タイムスタンプ
  * `update_now` (Bool; optional): 位置データの一時的な更新を強制します。コールバックで True に設定すると、ブラウザは位置データを更新し、update_now を False にリセットします。これは、例えばボタンやインターバルタイマーで位置を更新するために使用できます。
