`Parameters`型のコンストラクタ。パラメータのいくつかのサブタイプがODINNエコシステムの異なるパッケージで定義されているため、このコンストラクタは異なるサブタイプのコンストラクタを呼び出し、対応するサブタイプを持つ`Parameters`オブジェクトを返します。`Parameters`ミュータブル構造体は、抽象型を使用して`Sleipnir.jl`で定義されており、これらは後にODINNエコシステムの異なるパッケージで定義されます。

```
Parameters(;
        physical::PhysicalParameters = PhysicalParameters(),
        simulation::SimulationParameters = SimulationParameters(),
        solver::SolverParameters = SolverParameters(),
        hyper::Hyperparameters = Hyperparameters(),
        UDE::UDEparameters = UDEparameters()
        inversion::InversionParameters = InversionParameters()
        )
```

# キーワード引数

  * `physical::PhysicalParameters`: シミュレーションのための物理パラメータ。
  * `simulation::SimulationParameters`: シミュレーション設定に関連するパラメータ。
  * `solver::SolverParameters`: ソルバー設定のためのパラメータ。
  * `hyper::Hyperparameters`: モデルのためのハイパーパラメータ。
  * `UDE::UDEparameters`: UDE（普遍的微分方程式）特有のパラメータ。
  * `inversion::InversionParameters`: 逆プロセスのためのパラメータ。
