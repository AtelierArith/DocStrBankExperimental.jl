```
TreeMenu(root; pagesize::Int=10, dynamic = false, maxsize = pagesize, keypress = (m,i) -> false, kwargs...)
```

`root`を使用して、TerminalMenusを使ったインタラクティブメニューを作成します。`pagesize`はページに使用する行数です。`dynamic`がtrueの場合、コンテンツの展開に基づいてページサイズを調整します。`maxsize`はページの最大サイズです。

メニューが表示されている間にキーに応答するための関数`keypress`を提供します。この関数には2つの引数、`m::TreeMenu`と`i::UInt32`があります。整数`i`は押されたキーです。この関数は、メニューを終了すべき場合は`true`を、そうでない場合は`false`を返す必要があります。

`kwargs`は`TerminalMenus.Config`に渡されます。
