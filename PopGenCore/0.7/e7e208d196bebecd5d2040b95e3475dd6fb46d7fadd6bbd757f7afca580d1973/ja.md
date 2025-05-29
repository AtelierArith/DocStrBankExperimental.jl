```
locationdata!(data::PopData; longitude::Vector{Union{Missing,String}}, latitude::Vector{Union{Missing,String}})
```

既存の `PopData` 地理座標データを置き換えます。**十進分**または**度分秒**形式の `String` の `Vector` として受け取ります。テキストファイルから空間座標をインポートするには、`CSV.jl` の `CSV.read` を使用することをお勧めします。

## フォーマット要件

  * スペース（`"11 43 41"`）またはコロン（`"11:43:41"`）で区切られた `String` としての座標
  * 負の符号（`"-11 43.52"`）または単一文字の方位（`"11 43.52W"`）を使用する必要があります
  * 欠損データは文字列 `"missing"` としてコーディングする必要があります（`replace!()` を使用して実現できます）
  * コロンとスペースを混ぜることができます（ただし、これは悪い習慣です）

### 注意

座標データを4つのベクトル（経度の度、経度の分、緯度の度、緯度の分）として読み込んだ場合、最も簡単な方法は、それらを2つの文字列のベクトル（1つは経度、もう1つは緯度）にマージすることです：

```
long_string = string.(lat_deg, " ", lat_min)
lat_string = string.(long_deg, " ", long_min)
```

そして、これらを `locations!` への入力として使用します。

### 例

```
ncats = @nancycats;
x = fill("11 22.33W", 237) ; y = fill("-41 31.52", 237)
locationdata!(ncats, longitude = x, latitude = y)
```
