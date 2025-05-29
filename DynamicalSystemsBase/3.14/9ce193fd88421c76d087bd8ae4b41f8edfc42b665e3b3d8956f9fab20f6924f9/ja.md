```
DynamicalSystem
```

`DynamicalSystem`は、DynamicalSystems.jlライブラリにおける「動的システム」としてカウントされるすべての具体的な実装を包含する抽象スーパタイプです。

***`DynamicalSystem`のすべての具体的な実装は、[`step!`](@ref)関数を介して時間的に反復的に進化させることができます。*** したがって、システムを進化させるライブラリ関数のほとんどは、その現在の状態やパラメータを変更します。このことが並列化に与える影響については、オンラインのドキュメントを参照してください。

`DynamicalSystem`はさらに2つの抽象型に分かれています：`ContinuousTimeDynamicalSystem`、`DiscreteTimeDynamicalSystem`。`DynamicalSystem`の最も単純で一般的な具体的実装は、[`DeterministicIteratedMap`](@ref)または[`CoupledODEs`](@ref)です。

## 説明

`DynamicalSystem` **は状態空間における状態の時間的進化を表します**。主に3つのことをカプセル化しています：

1. 通常`u`と呼ばれる状態で、初期値は`u0`です。`u`が占める空間は`ds`の状態空間であり、`u`の長さは`ds`の次元（および状態空間の次元）です。
2. 通常`f`と呼ばれる動的ルールで、[`step!`](@ref)関数を呼び出すときに状態が時間とともにどのように進化/変化するかを決定します。`f`は通常、標準的なJulia関数であり、例についてはオンラインのドキュメントを参照してください。
3. `f`をパラメータ化するパラメータコンテナ`p`。`p`は何でも構いませんが、一般的には型安定な可変コンテナであることが推奨されます。

要するに、時間とともに変化する任意の量の集合は動的システムと見なすことができますが、`DynamicalSystem`の具体的なサブタイプはその範囲においてはるかに特定的です。具体的なサブタイプは通常、上記の3つの項目以上の情報を含んでいます。

この範囲では、動的システムには既知の動的ルール`f`があります。動的システムからの有限の*測定された*または*サンプリングされた*データは、[`StateSpaceSet`](@ref)を使用して表されます。このようなデータは、[`trajectory`](@ref)関数から取得されるか、未知の動的ルールを持つ動的システムの実験的測定から得られます。

動的システムを作成する例については、オンラインのDynamicalSystems.jlチュートリアルも参照してください。

## ModelingToolkit.jlとの統合

`DEProblem`から構築された動的システムは、ModelingToolkit.jlから構築されたものであり、シンボリックモデルとすべてのシンボリック変数への参照を保持します。シンボリック変数を使用して`DynamicalSystem`にアクセスすることは、[`observe_state`](@ref)、[`set_state!`](@ref)、[`current_parameter`](@ref)、および[`set_parameter!`](@ref)関数を介して可能です。動的システムに対応する参照されたMTKモデルは、`model = referrenced_sciml_model(ds::DynamicalSystem)`で取得できます。

例については、オンラインのDynamicalSystems.jlチュートリアルも参照してください。

!!! warn "初期条件とパラメータ"
    ModelingToolkit.jlは、すべての変数の初期条件を追加のパラメータとして扱います。これは、その用語が主に動的システムではなく初期値問題に向けられているためです。MTKモデルから動的システムを作成する際には、シンボルを介してのみパラメータにアクセスし、MTKモデルから問題タイプを作成する際に`split = false`キーワードを使用しないことを強く推奨します。


## API

`DynamicalSystem`が使用するAPIは、以下に示す関数で構成されています。`DynamicalSystem`のサブタイプの具体的なインスタンスを取得したら、次の関数を使用してクエリまたは変更できます。

具体的な動的システムインスタンスの主な使用目的は、ChaosTools.jlの`lyapunovspectrum`やAttractors.jlの`basins_of_attraction`などの下流関数に提供することです。典型的なユーザーは、動的システムを使用する新しいアルゴリズムの実装を開発している場合を除いて、以下のAPIを直接利用することはないでしょう。

### API - 情報を取得

  * `ds(t)`、ここで`ds`は`DynamicalSystem`のインスタンス：時間`t`における`ds`の状態を返します。連続時間システムの場合、これは現在および前の時間ステップを補間し、非常に正確です。離散時間システムの場合、`t`が現在の時間である場合にのみ機能します。
  * [`current_state`](@ref)
  * [`initial_state`](@ref)
  * [`observe_state`](@ref)
  * [`current_parameters`](@ref)
  * [`current_parameter`](@ref)
  * [`initial_parameters`](@ref)
  * [`isdeterministic`](@ref)
  * [`isdiscretetime`](@ref)
  * [`dynamic_rule`](@ref)
  * [`current_time`](@ref)
  * [`initial_time`](@ref)
  * [`isinplace`](@ref)
  * [`successful_step`](@ref)
  * [`referrenced_sciml_model`](@ref)

### API - 状態を変更

  * [`reinit!`](@ref)
  * [`set_state!`](@ref)
  * [`set_parameter!`](@ref)
  * [`set_parameters!`](@ref)
