factory(widget::Widget, bootstrap_method::TSBootMethod, nWidgets::Signed)

指定されたbootstrap_methodを使用してnWidgetsを作成します。タイプが「Stock」のウィジェットが渡された場合、ウィジェットファクトリは指定されたブートストラップメソッドを使用してn個の「Stock」ウィジェットを生成します。すべてのウィジェットは初差分を使用します。

## 位置引数

  * `widget::Widget`: 具体的なウィジェット構造体。詳細はウィジェットのドキュメントを参照してください。
  * `bootstrap_method`: TSBootMethodのサブタイプ：Stationary、MovingBlock、またはCircularBlock。
  * `nWidgets`: ウィジェットファクトリが返すウィジェットの数。

# 例

```julia
prices = [1,2,5,9,8,10,5,3];
widget = Stock(prices)

list_of_widgets = factory(widget, Stationary, 2)
```
