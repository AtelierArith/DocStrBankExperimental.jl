```
SeisWrite(filename,d,h,extent;<keyword arguments>)
```

地震データをseis形式で書き込みます

# 引数

  * `filename` : 書き込み/生成するファイルの名前
  * `d`: 地震データ
  * `h::Array{Header,1}`: Header型の要素を持つ1次元配列としてのヘッダー
  * `extent::Extent` : データの範囲（この情報を確認するには *names(Extent)* を試してください）
  * `itrace=1` : 書き込む最初のトレース番号

*クレジット: AS, 2015*
