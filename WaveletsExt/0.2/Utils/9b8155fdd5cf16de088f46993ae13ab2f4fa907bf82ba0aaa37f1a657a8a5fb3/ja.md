```
generatesignals(fn, L)
```

関数シンボル `fn` に基づいて、長さ 2ᴸ の信号を生成します。現在受け入れられている入力は、D. Donoho と I. Johnstone の "Adapting to Unknown Smoothness via Wavelet  Shrinkage" Preprint Stanford, January 93, p 27-28 に基づいています。

  * `:blocks`
  * `:bumps`
  * `:heavisine`
  * `:doppler`
  * `:quadchirp`
  * `:mishmash`

この関数のコードは、MATLAB の Wavelet Toolbox の `wnoise` 関数に基づいて適応および翻訳されています。

# 引数

  * `fn::Symbol`: 生成する関数/信号のタイプ。
  * `L::Integer`: (デフォルト = 7) 生成する信号のサイズ。サイズ 2ᴸ の信号を返します。

# 戻り値

`::Vector{Float64}`: 長さ 2ᴸ の信号。

# 例

```repl
using WaveletsExt

generatesignals(:bumps, 8)
```
