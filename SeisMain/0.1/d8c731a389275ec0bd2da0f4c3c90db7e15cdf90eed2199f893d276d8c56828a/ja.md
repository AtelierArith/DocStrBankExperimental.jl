```
SeisReadHeaders(filename;<keyword arguments>)
```

seisフォーマットの入力ファイルのヘッダーを読み取ります

# 引数

  * `group="all"` : オプションは all, some または gather
  * `key=[]`
  * `itrace=1` : 関数が読み取りを開始するトレースの番号
  * `ntrace=100` : 読み取るトレースの総数

# 例

```julia
h = SeisRead(filename)
```

*クレジット: AS, 2015*
