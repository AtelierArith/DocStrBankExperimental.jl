```
SimulatorForwardProblem{probType,obsType,configType,names} <: SciMLBase.AbstractSciMLProblem
```

パラメータ/初期条件から出力 `SimulatorObservable`s への「前方」問題を表します。このタイプは、基礎となる `SciMLProblem`、一連の `Observable`s、およびオプションの問題依存型の構成をラップします。

```
SimulatorForwardProblem(prob::SciMLBase.AbstractSciMLProblem, observables::SimulatorObservable...)
```

与えられた `AbstractSciMLProblem` から一般的なシミュレーター前方問題を構築します。これは任意の問題タイプ、例えば最適化問題、非線形システム、数値積分などである可能性があります。

```
SimulatorForwardProblem(f, p0::AbstractVector, observables::SimulatorObservable...)
```

与えられた関数または呼び出し可能な型 `f` と初期パラメータ `p0`、および与えられた `observables` から前方問題を作成します。

```
SimulatorForwardProblem(f, p0::AbstractVector)
```

与えられた関数または呼び出し可能な型 `f` と初期パラメータ `p0`、およびデフォルトの過渡的可観測量から前方問題を作成します。このコンストラクタは、可観測量の形状を決定するために `f(p0)` を呼び出します。もし `f` が非常にコストがかかり、これが望ましくない場合は、明示的なコンストラクタを使用することをお勧めします。
