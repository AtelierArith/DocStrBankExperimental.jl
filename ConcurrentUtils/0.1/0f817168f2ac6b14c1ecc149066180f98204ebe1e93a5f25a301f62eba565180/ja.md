```
@tasklet コード
```

`() -> コード` のメモ化バージョンでありながら、設定できない `Promise` のように振る舞うオブジェクトを作成します。

`t = @tasklet コード` は、`t()`、`fetch(t)`、`wait(t)`、および [`try_race_fetch`](@ref) をサポートします。

# 拡張ヘルプ

## 例

```jldoctest ConcurrentUtils0
julia> using ConcurrentUtils

julia> t = @tasklet begin
           println("呼び出し")
           123
       end;

julia> try_race_fetch(t)
Try.Err: NotSetError()

julia> t()
呼び出し
123

julia> t()
123

julia> fetch(t)
123

julia> wait(t);
```

## メモリ順序

タスクレット `t` から値を取得または待機するイベントは、`コード` 内のイベントからの発生前エッジを確立します。タスクレット `t` から値を取得または待機するイベントを含む API の呼び出しには、以下が含まれます：

  * `fetch(t)`
  * `wait(t)`
  * `try_race_fetch(t)` で `Ok` 結果を返すもの。

## サポートされている操作

タスクレット `t = @tasklet コード` は、以下の操作をサポートします：

  * `t()`: まだ評価されていない場合は `コード` を評価します。それ以外の場合は `fetch` と同等です。
  * `fetch(t)`: 他のタスクが `t()` を呼び出すのを待機し、その後結果を返します。
  * `wait(t)`: 他のタスクが `t()` を呼び出すのを待機します。
  * [`try_race_fetch`](@ref): すでに呼び出されている場合は `t()` の結果を取得しようとします。
