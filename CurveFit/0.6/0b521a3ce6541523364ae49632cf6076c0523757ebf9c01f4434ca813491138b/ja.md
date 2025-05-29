# 曲線フィッティングの一般的なインターフェース

同じ関数 `curve_fit` は、最初のパラメータで指定されたフィットタイプに応じてデータをフィットさせるために使用できます。この関数は、関数 `apply_fit` を使用してフィッティングモデルの値を推定するために使用できるオブジェクトを返します。

## いくつかの例:

  * `f = curve_fit(LinearFit, x, y)`
  * `f = curve_fit(Polynomial, x, y, n)`

他のフィットタイプには: LogFit, PowerFit, ExpFit, LinearKingFit, KingFit, RationalPoly が含まれます。詳細については、ドキュメントを参照してください。
