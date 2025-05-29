```
FORTRAN_format
```

FORTRANフォーマット指定子のフィールドに分解されたオブジェクト。

受け入れられる*データ型指定子*は： `Aw`,  `Iw`,  `Fw.d`,  `Ew.d`,  `Dw.d`

受け入れられる*出力フォーマット指定子*は： `Aw`,  `Iw.m`,  `Bw.m`,  `Ow.m`, `Zw.m`,  `Fw.d`,  `Ew.dEe`,  `ENw.d`,  `ESw.d`,  `Gw.dEe`,  `Dw.dEe`。表記： `w` - 幅、 `m`（オプション） - 最小桁数、 `d` - 小数点右の桁数、 `e` - 指数の桁数 `N`/`S`（オプション）は、`E`型の工学/科学フォーマットを示します。

フィールドは：

  * `.datatype`: プライマリFORTRANデータ型（`::String`）
  * `.char`: プライマリFORTRANデータ型文字（`::Char`）
  * `.EngSci`: 二次データ型文字 - Nは工学、Sは科学（`::Union{Char,Nothing}`）
  * `.width`: 数値フィールドの幅（`::Int`）
  * `.nmin`: 表示される最小桁数（`::Int`）
  * `.ndec`: 小数点右の桁数（`::Int`）
  * `.nexp`: 指数の桁数（`::Int`）
