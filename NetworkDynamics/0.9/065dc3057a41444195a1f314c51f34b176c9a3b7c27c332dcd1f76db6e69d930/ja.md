```
ComponentCondition(f::Function, sym, psym)
```

[`ComponentCallback`]のためのコールバック条件を作成します。

  * `f`: 条件関数。[`ContinousComponentCallback`](@ref)または[`DiscreteComponentCallback`](@ref)で使用する場合は`out=f(u, p, t)`の形式の関数である必要があり、[`VectorContinousComponentCallback`](@ref)で使用する場合は`f!(out, u, p, t)`である必要があります。

      * `f`の引数

          * `u`: 選択された`sym`状態の現在の値で、[`SymbolicView`](@ref)オブジェクトとして提供されます。
          * `p`: 選択された`psym`パラメータの現在の値。
          * `t`: 現在のシミュレーション時間。
  * `sym`: コンポーネントモデルの**状態**（入力、出力、観測を含む）を表すシンボルのベクターまたはタプル。コールバック条件関数`f`の引数`u`で利用可能な状態を決定します。
  * `psym`: コンポーネントモデルの**パラメータ**を表すシンボルのベクターまたはタプル。条件関数`f`で利用可能なパラメータを決定します。

# 例

状態`[:u1, :u2]`、入力`[:i]`、出力`[:o]`、およびパラメータ`[:p1, :p2]`を持つコンポーネントモデルを考えます。

```
ComponentCondition([:u1, :o], [:p1]) do u, p, t
    # 状態をシンボリックにまたは整数インデックスを介してアクセス
    u[:u1] == u[1]
    u[:o] == u[2]
    p[:p1] == p[1]
    # 状態/パラメータ`:u2`、`:i`、および`:p2`は
    # `sym`および`psym`引数にリストされていないため利用できません。
end
```
