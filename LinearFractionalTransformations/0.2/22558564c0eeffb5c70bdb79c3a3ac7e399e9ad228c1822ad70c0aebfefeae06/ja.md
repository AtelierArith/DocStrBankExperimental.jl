```
LFT
```

線形分数変換 `f(z)=(a*z+b)/(c*z+d)` で、`a,b,c,d` は複素数です。

コンストラクタ:

  * `LFT(a,b,c,d)`: 上記の関数を作成します。
  * `LFT()`: 恒等関数 `f(z) = z` を作成します。`LFT(1,0,0,1)` と同等です。
  * `LFT(a,b,c)`: `a ↦ 0`、`b ↦ 1`、`c ↦ ∞` の関数を作成します。
  * `LFT(a,aa,b,bb,c,cc)` または `LFT(a=>aa,b=>bb,c=>cc)`: `a ↦ aa`、`b ↦ bb`、`c ↦ cc` の関数を作成します。
