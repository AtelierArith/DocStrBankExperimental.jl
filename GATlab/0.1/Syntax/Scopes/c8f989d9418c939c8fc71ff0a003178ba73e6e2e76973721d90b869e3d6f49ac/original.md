A `Context` is anything which contains an ordered list of scopes.

Scopes within a context are referred to by *level*, which is their index within this list.

`Context`s should overload:

  * `getscope(c::Context, level::Int) -> Scope`
  * `nscopes(c::Context) -> Int`
  * `hastag(c::Context, tag::ScopeTag) -> Bool`
  * `hasname(c::Context, name::Symbol) -> Bool`
  * `getlevel(c::Context, tag::ScopeTag) -> Int`
  * `getlevel(c::Context, name::Symbol) -> Int`
  * `alltags(c::Context) -> Set{ScopeTag}`
