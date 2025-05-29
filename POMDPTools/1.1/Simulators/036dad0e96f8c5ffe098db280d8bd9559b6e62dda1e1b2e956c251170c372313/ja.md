```
sim(polfunc::Function, mdp::MDP; [<キーワード引数>])
sim(polfunc::Function, pomdp::POMDP; [<キーワード引数>])
```

各タイムステップでのアクションを計算する方法を指定する関数を使ってシミュレーションを実行する別の方法です。

# 使用法

```
sim(mdp) do s
    # 状態`s`に基づいてアクション`a`を計算するコード - これがポリシーです
    # 他にも何かを表示することができます
    return a
end
```

MDPの場合や

```
sim(pomdp) do o
    # 観測`o`に基づいて`a`を計算するコード
    # 必要に応じて、`o`をグローバル変数に保存したり、信念の更新を行ったりできます
    return a
end
```

POMDPの場合や

```
sim(pomdp, updater) do b
    # 信念`b`に基づいて`a`を計算するコード
    # `b`は`updater`によって計算されます
    return a
end
```

POMDPと信念アップデータの場合です。

# キーワード引数

## すべてのバージョン

  * `initialstate`: シミュレーションの初期状態
  * `simulator`: シミュレーションを実行するための任意のシミュレーターを指定するキーワード引数。シミュレーターが指定されていない場合、HistoryRecorderがシミュレーターとして使用され、すべてのキーワード引数がそれに転送されます。例えば、

    ```
    sim(mdp, max_steps=100, show_progress=true) do s
        # ...
    end
    ```

    はシミュレーションを100ステップに制限します。

## POMDPバージョン

  * `initialobs`: これはポリシー関数に与えられる初期観測を制御します。これが定義されていない場合、`rand(initialobs(m, s))`が利用可能であれば使用されます。利用できない場合は、`missing`が使用されます。

## POMDPおよびアップデータバージョン

  * `initialbelief`: `initialize_belief(updater, initialbelief)`はポリシー関数に与えられる最初の信念です。
