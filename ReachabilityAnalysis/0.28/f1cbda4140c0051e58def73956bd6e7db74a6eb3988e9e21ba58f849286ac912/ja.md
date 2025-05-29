```
normalize(system::AbstractSystem)
```

数学的システムを正規化（または標準）形式に変換します。

### 入力

  * `system` – システム; 離散または連続のいずれかです。

### 出力

すでに標準形式に適合している場合は同じシステム、そうでない場合は新しいシステム。

### 注意事項

正規化手順は、与えられたシステムタイプを内部で使用される「標準」形式に変換することから成ります。詳細は以下に示します。

### アルゴリズム

`normalize`の実装は、問題に関する情報を型パラメータとして持つ`MathematicalSystems`の型を利用します。

形式 $x' = Ax, x ∈ \mathcal{X}$ の同次ODEは、関連する問題が`ConstrainedLinearContinuousSystem`であり、`A`が行列である場合に標準です。このタイプは非決定的入力を扱いません。

`LinearContinuousSystem`は状態空間に対する制約（不変量など）を考慮しないことに注意してください。状態制約を指定するには、`ConstrainedLinearContinuousSystem`を使用します。渡されたシステムが`LinearContinuousSystem`（すなわち制約なし）である場合、正規化は制約集合として普遍集合（`Universe`）を固定します。

制約を持ち、時間変動の非決定的入力を持つ標準システムへの一般化が次に考慮されます。これらのシステムは形式 $x' = Ax + u, u ∈ \mathcal{U}, x ∈ \mathcal{X}$ です。システムタイプは`ConstrainedLinearControlContinuousSystem`であり、`A`は行列、`X`は集合、`U`は入力であり、すなわち`AbstractInput`の任意の具体的なサブタイプです。

`U`が入力として与えられない場合、正規化は`LazySet`または`LazySet`のベクトルのいずれかを受け入れます。これらの場合、集合は適切な具体的入力タイプでラップされます。

システムが標準形式に適合しない場合、実装は変換を試みます。そうでない場合はエラーがスローされます。特に、形式 $x' = Ax + Bu$ のODEは $x' = Ax + u, u ∈ B\mathcal{U}$ にマッピングされ、ここで $u$ は $x$ と同じ次元を持ちます。

上記の変換は離散の場合にも類似しており、すなわち線形およびアフィンの場合にそれぞれ $x_{k+1} = A x_k$ および $x_{k+1} = Ax_{k} + u_k, u_k ∈ \mathcal{U}, x_k ∈ \mathcal{X}$ です。
