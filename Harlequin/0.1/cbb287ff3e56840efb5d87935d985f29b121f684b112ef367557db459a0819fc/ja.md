```
genpointings!(sstr::ScanningStrategy, timerange_s, beam_dir, polangle_rad, result)
genpointings(sstr::ScanningStrategy, timerange_s, beam_dir, polangle_rad)
```

与えられた方向 `beam_dir`（3要素のベクトル）のボアサイトビームのための一連の指向方向と角度を生成します。これは、`sstr`のスキャン戦略を仮定しています。指向方向は、リスト `timerange_s` のすべての要素にわたって計算されます。角度 `polangle_rad` は、時刻 $t = 0$ における偏光角の値です。

2つの関数は、結果が呼び出し元に返される方法が異なるだけです。関数 `genpointings` は、次のフィールドを含む N×6 の行列を返します：

1. コラティチュード（ラジアン単位）
2. 経度（ラジアン単位）
3. 偏光角（ラジアン単位）
4. 一長さの指向ベクトルの X 成分
5. Y 成分
6. Z 成分

関数 `genpointings!` は `genpointings` のように動作しますが、事前に割り当てられた行列を入力として受け取り（`result` パラメータ）、その中に結果を保存します。行列は、少なくともサイズ `(N, 6)` の2次元でなければなりません。

両方の関数は、[`time2pointing!`](@ref) と [`time2pointing`](@ref) をラップするシンプルなイテレータです。
