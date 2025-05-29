```
fdm(x::Vector; scheme::Symbol = :central)
```

`x`に適用される有限差分法（FDM）。

**引数:**

  * `x`:      データベクトル
  * `scheme`: （オプション）使用される有限差分法のスキーム

      * `backward`:  1階導関数 1次後方差分
      * `forward`:   1階導関数 1次前方差分
      * `central`:   1階導関数 2次中心差分
      * `backward2`: 1階導関数 2次後方差分
      * `forward2`:  1階導関数 2次前方差分
      * `fourth`:    4階導関数中心差分

**戻り値:**

  * `dif`: 有限差分のベクトル（`x`の長さ）
