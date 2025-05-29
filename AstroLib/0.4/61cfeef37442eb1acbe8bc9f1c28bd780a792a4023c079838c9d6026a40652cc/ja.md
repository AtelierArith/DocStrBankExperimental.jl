```
adstring(ra::Real, dec::Real[, precision::Int=2, truncate::Bool=true]) -> string
adstring([ra, dec]) -> string
adstring(dec) -> string
adstring([ra], [dec]) -> ["string1", "string2", ...]
```

### 目的

右昇と赤緯を性分数形式の文字列として返します。

### 説明

小数形式で表現された右昇と赤緯を受け取り、それを性分数に変換してフォーマットされた文字列を返します。 右昇と赤緯の精度を指定できます。

### 引数

この関数の引数は次のとおりです：

  * `ra`: 小数度での右昇。印刷前に時間に変換されます。
  * `dec`: 小数度での赤緯。

関数は異なる方法で呼び出すことができます：

  * 2つの数値引数：最初が`ra`、2番目が`dec`です。
  * 2つの要素のイテラブル（配列、タプル）：`(ra, dec)`。
  * 1つの数値引数：`dec`のみが提供されていると仮定されます。

出力形式に影響を与えるオプションのキーワードは常に利用可能です：

  * `precision`（オプションの整数キーワード）：赤緯秒の桁数を指定します。右昇秒の桁数は常に`precision`より1桁多いと仮定されます。入力として`dec`のみが与えられた場合、`precision`はデフォルトで1、他のケースではデフォルトで0になります。
  * `truncate`（オプションのブールキーワード）：trueの場合、出力の最後に表示される桁は丸められるのではなく精度で切り捨てられます。このオプションは、座標指定を伴う公式IAU名を形成するために`adstring`が使用される場合に便利です（http://vizier.u-strasbg.fr/Dic/iau-spec.htxを参照）。

### 出力

関数は1つの文字列を返します。文字列の形式は、上記の`precision`および`truncate`キーワードで指定できます。

### 例

```jldoctest
julia> using AstroLib

julia> adstring(30.4, -1.23, truncate=true)
" 02 01 35.9  -01 13 48"

julia> adstring.([30.4, -15.63], [-1.23, 48.41], precision=1)
2-element Vector{String}:
 " 02 01 36.00  -01 13 48.0"
 " 22 57 28.80  +48 24 36.0"
```
