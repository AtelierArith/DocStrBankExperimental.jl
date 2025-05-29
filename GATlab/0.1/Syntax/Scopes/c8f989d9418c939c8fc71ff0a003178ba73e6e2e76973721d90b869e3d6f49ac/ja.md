`Context`は、順序付けられたスコープのリストを含むものです。

コンテキスト内のスコープは*レベル*によって参照され、これはこのリスト内でのインデックスです。

`Context`は以下をオーバーロードする必要があります：

  * `getscope(c::Context, level::Int) -> Scope`
  * `nscopes(c::Context) -> Int`
  * `hastag(c::Context, tag::ScopeTag) -> Bool`
  * `hasname(c::Context, name::Symbol) -> Bool`
  * `getlevel(c::Context, tag::ScopeTag) -> Int`
  * `getlevel(c::Context, name::Symbol) -> Int`
  * `alltags(c::Context) -> Set{ScopeTag}`
