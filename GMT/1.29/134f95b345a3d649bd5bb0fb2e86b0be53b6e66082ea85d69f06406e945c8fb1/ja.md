```
wmsinfo(server::String)
```

WebMapServerサービスからxml情報を読み取り、データをダウンロードするために必要な情報を保持するWMSデータ型を作成します。`show`メソッドはWMSデータ型の内容を表示します。

  * `server`: サーバーのURLアドレス。

## 例

```
wms = wmsinfo("http://tiles.maps.eox.at/wms?")
```

オプションとして、次の形式を使用して

```
wmsinfo(wms; layer)
```

レイヤー番号またはレイヤー名`layer`のバンド数やサイズなどのさらなる情報を取得します。`wms`は最初の形式で返されます。
