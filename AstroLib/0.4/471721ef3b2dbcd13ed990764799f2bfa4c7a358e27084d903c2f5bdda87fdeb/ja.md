```
euler(ai, bi, select[, FK4=true, radians=true])
```

### 目的

銀河座標、天体座標、黄道座標の間で変換します。

### 説明

この関数はastro手続きによって使用されます。

### 引数

  * `ai`: 入力経度、スカラーまたはベクトル。
  * `bi`: 入力緯度、スカラーまたはベクトル。
  * `select` : 座標変換のタイプを指定する整数入力。 SELECT   From          To     | SELECT   From       To    1   RA-Dec (2000) Galactic |   4    Ecliptic   RA-Dec    2   Galactic      RA-DEC   |   5    Ecliptic   Galactic    3   RA-Dec        Ecliptic |   6    Galactic   Ecliptic
  * `FK4` (オプションのブールキーワード) : このキーワードが`true`に設定されている場合、入力および出力の天体座標と黄道座標は、等分点B1950で与えられるべきです。`false`の場合、デフォルトでは等分点J2000で与えられるべきです。
  * `radians` (オプションのブールキーワード) : このキーワードが`true`に設定されている場合、すべての入力および出力の角度は度ではなくラジアンで表されます。

### 出力

2つのタプル `(ao, bo)`:

  * `ao`: 出力経度（度）。
  * `bo`: 出力緯度（度）。

### 例

Cyg X-1の銀河座標を求める (ra=299.590315, dec=35.201604)

```jldoctest
julia> using AstroLib

julia> euler(299.590315, 35.201604, 1)
(71.33498957116959, 3.0668335310640984)
```

### 注意事項

この関数のコードはIDL天文学ユーザーライブラリに基づいています。
