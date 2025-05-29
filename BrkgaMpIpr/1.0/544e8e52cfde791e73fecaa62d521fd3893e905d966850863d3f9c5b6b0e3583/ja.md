```
function path_relink!(brkga_data::BrkgaData,
    pr_type::PathRelinkingType,
    pr_selection::PathRelinkingSelection,
    compute_distance::Function,
    affect_solution::Function,
    number_pairs::Int64,
    minimum_distance::Float64,
    block_size::Int64,
    max_time::Float64,
    percentage::Float64
)::PathRelinkingResult
```

エリートソリューション間で、少なくとも指定された最小距離があるパスリリンクを実行します。

複数の集団が存在する場合、パスリリンクは異なる集団のエリートクロモソーム間で円環状に実行されます。たとえば、3つの集団があるとします。このフレームワークは3回のパスリリンクを実行します：最初は集団1と集団2の個体間、次は集団2と集団3の間、最後は集団3と集団1の間です。1つの集団だけの場合、基準個体とガイド個体はその集団のエリートセットからサンプリングされます。

アルゴリズムは、距離関数によって与えられた最小距離を持つ基準ソリューションとガイドソリューションのペアを見つけようとします。これが不可能な場合、新しいソリューションのペアがサンプリングされ（重複なしで）、距離に対してテストされます。指定された集団に対してそのようなペアを見つけることができない場合、アルゴリズムは次の集団ペアにスキップします（上記のように円環状に）。しかし、どのケースでもそのようなペアが見つからない場合、アルゴリズムは失敗を宣言します。これは、集団が非常に均質であることを示しています。

見つかったソリューションがこれまでに見つかった最良のソリューションである場合、IPRは最悪のソリューションをそれに置き換えます。そうでない場合、IPRは見つかったソリューションとエリートセット内の他のすべてのソリューションとの距離を計算し、見つかったソリューションがすべてのソリューションから少なくとも`minimum_distance`離れている場合にのみ、最悪のソリューションをそれに置き換えます。

APIは常に`decode!()`関数を`writeback = false`で呼び出します。理由は、デコーダーがクロモソームを書き換えると、ソリューション間のパスが失われ、意図しない結果が生じる可能性があるためです。パスリリンクの最後に、メソッドは見つかった最良のクロモソームで`writeback = true`を使用してデコーダーを呼び出し、このクロモソームが見つかった最良のソリューションを反映するように再書き込まれることを保証します。

このメソッドはマルチスレッド実装です。各クロモソームを1つずつ構築してデコードするのではなく、メソッドは候補のリストを構築し、ガイドソリューションに従ってアレル/キーを変更し、その後すべての候補を並行してデコードします。候補を構築するためには`O(chromosome_size^2 / block_size)`の追加メモリが必要であり、`chromosome_size`が非常に大きい場合はコストがかかる可能性があります。

!!! warning
    [`evolve!()`](@ref)と同様に、デコーディングはスレッドを使用して並行して行われ、ユーザーは**デコーダーがスレッドセーフであることを保証しなければなりません。** そのような特性を保持できない場合は、環境変数`JULIA_NUM_THREADS = 1`を設定してシングルスレッドを使用することをお勧めします [(Julia Parallel Computingを参照)](https://docs.julialang.org/en/v1.1/manual/parallel-computing/)。


# 引数

  * [`brkga_data::BrkgaData`](@ref BrkgaData): BRKGAデータ。
  * [`pr_type::PathRelinkingType`](@ref PathRelinkingType): 実行するパスリリンクのタイプ。`DIRECT`または`PERMUTATION`ベースのいずれか。
  * [`pr_selection::PathRelinkingSelection`](@ref PathRelinkingSelection): パスリリンクに使用する個体の選択。`BESTSOLUTION`または`RANDOMELITE`のいずれか。
  * `compute_distance::Function`: 2つのクロモソーム間の距離を計算するために使用される関数。この関数は**次のシグネチャを持っている必要があります**

    ```julia
    compute_distance(vector1::Array{Float64, 1},
                     vector2::Array{Float64, 1})::Float64
    ```
  * `affect_solution::Function`: 2つの部分クロモソーム/遺伝子ブロック`block1`と`block2`を受け取り、`block1`から`block2`へのキーの変更がソリューションに影響を与えるかどうかをチェックする関数。たとえば、アレル/キーがしきい値として使用され、値が> 0.5で機能をアクティブにするとします。`block1 = [0.3, 0.4, 0.1]`および`block2 = [0.4, 0.1, 0.2]`があるとします。すべての値が0.5未満であるため、`block1`から`block2`へのキーの変更はソリューションを変更せず、そのため、その変更（およびその後のデコーディング）をドロップできます。ブロックは、1つのキー/アレル、連続したキーのブロック、または全クロモソームのみを保持できます。`affect_solution`は2つのビュー/サブアレイを受け取ります。この関数は**次のシグネチャを持っている必要があります**

    ```julia
    affect_solution(block1::SubArray{Float64, 1},
                    block2::SubArray{Float64, 1})::Bool
    ```

    !!! note
        この関数は問題の構造とキー/アレルの使用方法に依存します
  * `number_pairs::Int64`: テストされるクロモソームペアの数。`number_pairs < 1`の場合、すべてのペアがテストされます。
  * `minimum_distance::Float64`: `compute_distance`によって計算された2つのクロモソーム間の最小距離。
  * `block_size::Int64 = 1`: 各イテレーションで一度に交換されるアレルの数。1の場合、従来のパスリリンクが実行されます。1以上でなければなりません。
  * `max_time::Float64 = 0`: `max_time`に達したときにパスリリンクを中止します。`max_time ≤ 0`の場合、制限は課されません。秒単位で指定されます。
  * `percentage::Float64 = 1.0`: 構築するパスのサイズをパーセンテージで定義します。範囲[0, 1]。

# 戻り値

  * リリンクの状態に応じて[`PathRelinkingResult`](@ref)を返します。

# 例外をスロー

  * `ErrorException`: [`initialize!()`](@ref)が呼び出されていない場合。
  * `ArgumentError`: `percentage < 1e-6 || percentage > 1.0`かつ`block_size < 1`の場合。
