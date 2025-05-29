```
ComponentAffect(f::Function, sym, psym)
```

[`ComponentCallback`]のコールバック条件を作成します。

  * `f`: 影響関数。`f(u, p, [event_idx], ctx)`の形式の関数でなければなりません。ここで、`event_idx`は[`VectorContinousComponentCallback`](@ref)の場合にのみ利用可能です。

      * `f`の引数

          * `u`: 選択された`sym`状態の現在の（可変）値で、[`SymbolicView`](@ref)オブジェクトとして提供されます。
          * `p`: 選択された`psym`パラメータの現在の（可変）値。
          * `event_idx`: 現在のイベントインデックス、すなわち[`VectorContinousComponentCallback`](@ref)の場合にトリガーされた`out`要素。
          * `ctx::NamedTuple` コンテキスト変数を持つ名前付きタプル。

              * `ctx.model`: コンポーネントモデルへの参照
              * `ctx.vidx`/`ctx.eidx`: 頂点/エッジモデルのインデックス。
              * `ctx.src`/`ctx.dst`: srcおよびdstインデックス（エッジモデルのみ）。
              * `ctx.integrator`: インテグレーターオブジェクト。ネットワークを取得するには[`extract_nw`](@ref)を使用します。
              * `ctx.t=ctx.integrator.t`: 現在のシミュレーション時間。
  * `sym`: コンポーネントモデルの**状態**（**入力、出力、観測を除く**）を表すシンボルのベクターまたはタプル。コールバック条件関数`f`のパラメータ`u`を通じて利用可能な状態を決定します。
  * `psym`: コンポーネントモデルの**パラメータ**を表すシンボルのベクターまたはタプル。条件関数`f`で利用可能なパラメータを決定します。

# 例

状態`[:u1, :u2]`、入力`[:i]`、出力`[:o]`、パラメータ`[:p1, :p2]`を持つコンポーネントモデルを考えます。

```
ComponentAffect([:u1, :o], [:p1]) do u, p, ctx
    u[:u1] = 0 # 状態を変更
    p[:p1] = 1 # パラメータを変更
    @info "頂点 $(ctx.vidx) で :u1 と :p1 を変更しました" # コンテキストにアクセス
end
```
