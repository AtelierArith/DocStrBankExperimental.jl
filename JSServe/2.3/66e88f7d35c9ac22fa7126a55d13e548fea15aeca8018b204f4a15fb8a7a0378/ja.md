```
App(callback_or_dom; title="JSServe App")
App((session, request) -> DOM.div(...))
App((session::Session) -> DOM.div(...))
App((request::HTTP.Request) -> DOM.div(...))
App(() -> DOM.div(...))
App(DOM.div(...))
```

使用法:

```julia
using JSServe
app = App() do
    return DOM.div(DOM.h1("こんにちは世界"), js"""console.log('こんにちは世界')""")
end
```

グローバルオブザーバブルに依存する場合は、それをセッションにバインドすることを確認してください。これは非常に重要です。アプリを表示するたびに、リスナーがそれに登録され、Juliaプロセスが終了するまでそこに留まり続けます。`bind_global`は、オブザーバブルをセッションのライフサイクルにバインドし、アプリが表示されなくなった後に状態をクリーンアップすることでそれを防ぎます。`App`を`Server`経由で提供する場合、これらのグローバルはページを訪れるすべての人と共有されるため、同時に多くのユーザーによって使用される可能性があります。

```julia
global some_observable = Observable("グローバルこんにちは世界")
App() do session::Session
    bound_global = bind_global(session, some_observable)
    return DOM.div(bound_global)
end
```
