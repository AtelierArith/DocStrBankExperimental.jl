```
mutable struct BrkgaData
```

BRKGA-MP-IPRアルゴリズムの内部状態を表します。

この構造体には直接のコンストラクタはなく、[`build_brkga`](@ref)関数を使用して構築する必要があります。アルゴリズムの異なる状態を表す複数の`BrkgaData`を作成し、それらを独立して使用できます。

!!! warning
    この構造体は**BRKGA関数の外部で使用することを意図していません**。アドホックな変更は意図しない結果を招く可能性があります。


## フィールド

  * `opt_sense`: 最適化の感覚（最小化 = 0、最大化 = 1）。
  * `chromosome_size`: 染色体内の遺伝子の数 [> 0]。
  * `params`: 進化のためのBRKGAパラメータ。
  * `elite_size`: 集団内のエリート項目の数 [> 0]。
  * `num_mutants`: 各世代で集団に導入される突然変異体の数 [> 0]。
  * `evolutionary_mechanism_on`: falseの場合、進化は行われず、染色体のデコードのみが行われます。マルチスタートアルゴリズムをエミュレートするのに非常に便利です。
  * `problem_instance`: *(内部データ)* 染色体を問題の解にマッピングするために`decode!`関数によって使用される問題インスタンス。このデータは`decode!`によって変更されるべきではないため、この属性は定数と見なすことができます。
  * `decode!`: *(内部データ)* 進化プロセスおよびパスリリンク中に呼び出される**主要なデコード関数**です。次のシグネチャを**持たなければなりません**：

    ```julia
    decode!(chromosome::Array{Float64, 1},
            problem_instance::AbstractInstance,
            rewrite::Bool = true)::Float64
    ```

    `rewrite == false`の場合、`decode!`は`chromosome`を変更してはなりません。IPRルーチンは`decode!`が`chromosome`を変更しないことを要求します。
  * `rng`: *(内部データ)* 内部乱数生成器の番号。外部で使用しないでください。RNGが必要な場合は、新しい生成器を作成してください。
  * `previous`: *(内部データ)* 前の集団。
  * `current`: *(内部データ)* 現在の集団。
  * `bias_function`: *(内部データ)* `bias_function(::Int64 > 0)::Float64`となる単調非増加関数。
  * `total_bias_weight`: *(内部データ)* バイアス関数に基づく各ランキングの結果の合計を保持します。この値は正規化に必要です。
  * `shuffled_individuals`: *(内部データ)* 交配中に個体/染色体のインデックスをシャッフルするために使用されます。
  * `parents_ordered`: *(内部データ)* 交配中の親の順序を定義します。
  * `initialized`: *(内部データ)* アルゴリズムが適切に初期化されたかどうかを示します。
  * `reset_phase`: *(内部データ)* アルゴリズムがリセットされたかどうかを示します。
