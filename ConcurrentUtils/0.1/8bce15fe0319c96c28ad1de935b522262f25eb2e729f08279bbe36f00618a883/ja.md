```
Promise{T}()
Promise()
```

型 `T` のプロミスを作成します。つまり、型 `T` の値を一度設定し、非同期に取得できるメモリ位置を保持します。

# 拡張ヘルプ

この概念の説明については、[Futures and promises - Wikipedia](https://en.wikipedia.org/wiki/Futures_and_promises)を参照してください。

## 例

```jldoctest Promise
julia> using ConcurrentUtils

julia> p = Promise{Int}();

julia> try_race_fetch(p)
Try.Err: NotSetError()

julia> put!(p, 123);

julia> fetch(p)
123

julia> try_race_put!(p, 456)
Try.Err: 123
```

## メモリ順序

`promise` から値を取得または待機するイベントは、その値を `promise` に設定したイベントからの発生前のエッジを確立します。値を `promise` に設定するイベントを含むAPIの呼び出しには以下が含まれます：

  * `put!(promise, value)` は例外をスローしません。
  * `try_race_put!(promise, value)` は `Ok` 結果を返します。
  * `try_race_put_with!(thunk, promise)` は `thunk` を呼び出します（したがって `Ok` を返します）。
  * `race_put_with!(thunk, promise)` は `thunk` を呼び出します。

（呼び出し `thunk()` は値を設定するイベントの前に順序付けられます。）

`promise` から値を取得または待機するイベントを含むAPIの呼び出しには以下が含まれます：

  * `fetch(promise)`
  * `wait(promise)`
  * `try_race_fetch(promise)` は `Ok` 結果を返します。
  * `try_race_put_with!(thunk, promise)` は `thunk` を呼び出さない（したがって `Err` を返します）
  * `race_put_with!(thunk, promise)` は `thunk` を呼び出さない

## サポートされている操作

`promise::Promise{T}` は以下の操作をサポートします：

  * `put!(promise, value)`: `value` を設定します。すでに値が設定されている場合はエラーをスローします。
  * [`try_race_put!(promise, value)`](@ref try_race_put!): `value` を設定しようとします。
  * `fetch(promise)`: `promise` が保持している値を取得します。必要に応じて待機します。
  * `wait(promise)`: 値が設定されるのを待ちます。
  * [`try_race_fetch(promise)`](@ref try_race_fetch): `promise` に存在する値を取得しようとします。
  * [`try_race_put_with!(thunk, promise)`](@ref try_race_put_with!): `thunk` によって生成された値を取得または設定しようとします。
  * [`race_put_with!(thunk, promise)`](@ref): `try_race_put_with!` に似ていますが、返される値は `thunk` が呼び出されたかどうかを示しません。
