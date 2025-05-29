`WindowType`は、X線ウィンドウのモデルまたはタイプの抽象型です。これらのタイプは、ウィンドウのタイプと実装を区別します。多くの場合、ベンダーからの表形式の透過関数と、ウィンドウの構造に基づいて計算された透過関数の両方があります。`TabulatedWindow`または`ModeledWindow`を使用して、`transmission(wnd::AbstractWindow, energy::Float64, angle::Float64 = π / 2)`メソッドを実装する`AbstractWindow`をインスタンス化します。

定義済みの`WindowType`は、`MoxtekAP33`、`MoxtekAP5`、`AmptekC1`、`AmptekC2`、`BerylliumWindow`です。
