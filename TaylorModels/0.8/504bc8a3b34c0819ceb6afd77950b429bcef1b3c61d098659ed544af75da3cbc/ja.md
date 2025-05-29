rpa(g::Function, tmf::TaylorModel1)    rpa(g::Function, tmf::RTaylorModel1)    rpa(g::Function, tmf::TaylorModelN)

関数 `g` のための厳密多項式近似 (RPA) は、絶対/相対残差 `tmf` を持つテイラーモデルを使用します。境界は可能であれば単調性を利用して計算され、それ以外の場合はラグランジュ境界を使用します。
