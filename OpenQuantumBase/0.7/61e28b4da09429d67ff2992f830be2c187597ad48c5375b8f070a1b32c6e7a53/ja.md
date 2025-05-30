```julia
struct DiffEqLiouvillian{diagonalization, adiabatic_frame}
```

ソルバーに供給するための全体リウビリアンを定義します。`DiffEqOperator`インターフェースを使用します。閉じた系と開いた系のリウビリアンの両方を含みます。

# フィールド

  * `H`: ハミルトニアン
  * `opensys_eig`: 固有基底における開いた系
  * `opensys`: 正規基底における開いた系
  * `lvl`: 切り捨てるレベル
  * `digits`: ゼロギャップ値の丸めに使用する桁数
  * `sigdigits`: ギャップの丸めに使用する有効桁数
  * `u_cache`: 内部キャッシュ
