```
ccifrm(frclss, clssid)
```

与えられたフレームクラスとクラスIDに関連付けられたフレーム名、フレームID、および中心を返します。

### 引数

  * `frclss`: フレームのクラス
  * `clssid`: フレームのクラスID

### 出力

フレームが見つからなかった場合は `nothing` を返すか、

  * `frcode`: フレームのIDコード
  * `frname`: フレームの名前
  * `center`: フレームの中心のIDコード

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ccifrm_c.html)
