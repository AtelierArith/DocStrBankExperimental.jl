```
App(callback_or_dom; title="JSServe App")
App((session, request) -> DOM.div(...))
App((session::Session) -> DOM.div(...))
App((request::HTTP.Request) -> DOM.div(...))
App(() -> DOM.div(...))
App(DOM.div(...))
```

Usage:

```julia
using JSServe
app = App() do
    return DOM.div(DOM.h1("hello world"), js"""console.log('hello world')""")
end
```

If you depend on global observable, make sure to bind it to the session. This is pretty important, since every time you display the app, listeners will get registered to it, that will just continue staying there until your Julia process gets closed. `bind_global` prevents that by binding the observable to the life cycle of the session and cleaning up the state after the app isn't displayed anymore. If you serve the `App` via a `Server`, be aware, that those globals will be shared with everyone visiting the page, so possibly by many users concurrently.

```julia
global some_observable = Observable("global hello world")
App() do session::Session
    bound_global = bind_global(session, some_observable)
    return DOM.div(bound_global)
end
```
