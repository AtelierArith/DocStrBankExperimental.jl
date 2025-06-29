```
function esdc(;kwargs...)
```

AWSからデータキューブをデータセットとして開きます。これはどのシステムでも機能しますが、接続速度に応じて遅延が発生する可能性があります。`bucket`と`store`を指定するか、解像度、チャンク化、キューブ領域を選択することができます。

### キーワード引数

  * `bucket=nothing` 例として"obs-esdc-v2.0.0"のOBSバケットを指定します
  * `store=""` 例として"esdc-8d-0.25deg-184x90x90-2.0.0.zarr"のキューブのルートパスを指定します
  * `res="low"` データキューブの解像度を選択します（`"low"`または`"high"`）
  * `chunks="ts"` チャンク化を選択します（時間系列アクセスのための`"ts"`または空間分析のための`"map"`）
  * `region="global"` データキューブを選択します（`"global"`または`"Colombia"`）
