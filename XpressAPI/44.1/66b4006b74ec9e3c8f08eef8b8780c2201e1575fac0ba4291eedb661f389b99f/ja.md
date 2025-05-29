```
XPRSloadmiqp64(prob, probname, ncols, nrows, rowtype, rhs, rng, objcoef, start, collen, rowind, rowcoef, lb, ub, nobjqcoefs, objqcol1, objqcol2, objqcoef, nentities, nsets, coltype, entind, limit, settype, setstart, setind, refval)::prob
```

MIQP問題、すなわち二次目的係数を持つMIPをOptimizerデータ構造にロードするために使用されます。

整数、バイナリ、部分整数、半連続および半連続整数変数を定義でき、タイプ1および2のセットとともに使用できます。セットメンバーの参照行値は、参照行を指定するのではなく、配列として渡されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `probname::Union{Nothing,AbstractString}`: 問題の名前を含む最大MAXPROBNAMELENGTH文字の文字列。
  * `ncols::Integer`: 行列の構造列の数。
  * `nrows::Integer`: 行列の行数（目的を含まない）。
  * `rowtype::AbstractVector{Cchar}`: 行タイプを含む長さ`nrows`の文字配列: Lは`<=`制約を示す; Eは=制約を示す; Gは`>=`制約を示す; Rは範囲制約を示す; Nは非拘束制約を示す。
  * `rhs::AbstractVector{Number}`: 右辺係数を含む長さ`nrows`の倍精度配列。
  * `rng::AbstractVector{Number}`: 範囲行の範囲値を含む長さ`nrows`の倍精度配列。
  * `objcoef::AbstractVector{Number}`: 目的関数係数を含む長さ`ncols`の倍精度配列。
  * `start::AbstractVector{Integer}`: 各列の要素の開始位置を示す`rowind`および`rowcoef`配列のオフセットを含む整数配列。
  * `collen::AbstractVector{Integer}`: 各列の非ゼロ要素の数を含む長さ`ncols`の整数配列。
  * `rowind::AbstractVector{Integer}`: 各列の非ゼロ要素の行インデックスを含む整数配列。
  * `rowcoef::AbstractVector{Number}`: `rowind`と同じ長さの非ゼロ要素値を含む倍精度配列。
  * `lb::AbstractVector{Number}`: 列の下限を含む長さ`ncols`の倍精度配列。
  * `ub::AbstractVector{Number}`: 列の上限を含む長さ`ncols`の倍精度配列。
  * `nobjqcoefs::Integer`: 二次項の数。
  * `objqcol1::AbstractVector{Integer}`: 各二次項の最初の変数の列インデックスを含むサイズ`nobjqcoefs`の整数配列。
  * `objqcol2::AbstractVector{Integer}`: 各二次項の2番目の変数の列インデックスを含むサイズ`nobjqcoefs`の整数配列。
  * `objqcoef::AbstractVector{Number}`: 二次係数を含むサイズ`nobjqcoefs`の倍精度配列。
  * `nentities::Integer`: バイナリ、整数、半連続、半連続整数および部分整数エンティティの数。
  * `nsets::Integer`: SOS1およびSOS2セットの数。
  * `coltype::AbstractVector{Cchar}`: エンティティタイプを含む長さ`nentities`の文字配列: Bはバイナリ変数; Iは整数変数; Pは部分整数変数; Sは半連続変数; Rは半連続整数。
  * `entind::AbstractVector{Integer}`: MIPエンティティの列インデックスを含む長さ`nentities`の整数配列。
  * `limit::AbstractVector{Number}`: 部分整数変数の整数制限および半連続および半連続整数変数の下限を含む長さ`nentities`の倍精度配列（バイナリおよび整数変数に対応する位置のエントリは無視されます）。
  * `settype::AbstractVector{Cchar}`: 1はSOS1タイプセット; 2はSOS2タイプセットを含む長さ`nsets`の文字配列。必要ない場合は`nothing`である可能性があります。
  * `setstart::AbstractVector{Integer}`: セットの開始を示す`setind`および`refval`配列のオフセットを含む整数配列。
  * `setind::AbstractVector{Integer}`: 各セットの列を含む長さ`setstart[nsets]-1`の整数配列。
  * `refval::AbstractVector{Number}`: 各セットメンバーの参照行エントリを含む長さ`setstart[nsets]-1`の倍精度配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSloadmiqp64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadmiqp64.html)のドキュメントも参照してください。
