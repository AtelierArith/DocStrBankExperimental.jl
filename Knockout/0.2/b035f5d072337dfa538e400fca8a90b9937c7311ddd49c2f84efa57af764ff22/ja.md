`knockout(template, data=Dict(), extra_js = js""; computed = [], methods = [])`

Knockoutスコープを作成し、`template`によって提供されたHTML構造を`data`で埋めます。

# 引数

  * `template`はテンプレートとして機能する`Node`です。 [Knockout構文](http://knockoutjs.com/documentation/value-binding.html)を参照してください。
  * `data`は辞書または`propertyName => value`ペアの配列です。

プロパティの値がobservableである場合、この関数は自動的にJulia -> JS通信を設定します。JSからJulia通信を設定するには、スコープをレンダリングする*前に* `scope[propertyName]`にイベントハンドラーを設定します（`on(f, scope[propertyName])`を呼び出すことによって）。他のobservableの関数として計算されるようにしたいKnockoutのobservableを指定できます。例えば、`knockout(...; computed = Dict(:fullName => @js function(){this.firstName() + ' ' + this.lastName()}))`のように指定できます。Knockoutスコープで利用可能にしたい関数をキーワード引数として`knockout`に渡すことができます。例えば、`knockout(...; methods=Dict(:sayhello=>@js function(){ alert("hello!") }))`のように指定できます。
