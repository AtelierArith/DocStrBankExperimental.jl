```
sf36(v; version = :v1)
```

ベクトルの回答 `v` に対して SF36 結果を計算します。

version キーワード:

  * `:v1` - 一般的な米国人口 (Ware, John & MA, Kosinski & Keller, S.D.. (1993). SF-36 Physical and Mental Health Summary Scales: a User's Manual. 8. 23-28.)
  * `:v2` - 相関スコア (Grassi, M. and Nucera, A. (2010), Dimensionality and Summary Measures of the SF-36 v1.6: Comparison of Scale- and Item-Based Approach Across ECRHS II Adults Population. Value in Health, 13: 469-478.)

ベクトル `v`:

1,33:36 - 一般的健康(GH) - 1, 11a:11d

3:12 - 身体機能 (PF) - 3a:3j

13:16 - 役割-身体機能 (RP) - 4a:4d

17:19 - 役割-感情 (RE) - 5a:5c

20,32 - 社会的機能 (SF) - 6,10

21,22 - 身体の痛み (BP) - 7,8

24:26,28,30 - メンタルヘルス (MH) - 9b:9d, 9f, 9h

23,27,29,31 - 活力 (VT) - 9a, 9e, 9g, 9i 
