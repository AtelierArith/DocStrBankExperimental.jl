```julia
dynamics!(result, state; ...)
dynamics!(result, state, torques; ...)
dynamics!(
    result,
    state,
    torques,
    externalwrenches;
    stabilization_gains
)

```

関節空間の運動方程式を満たす関節加速度ベクトル $\dot{v}$ とラグランジュ乗数 $\lambda$ を計算します。

$$
M(q) \dot{v} + c(q, v, w_\text{ext}) = \tau - K(q)^{T} \lambda
$$

および制約方程式

$$
K(q) \dot{v} = -k
$$

与えられた関節構成ベクトル $q$、関節速度ベクトル $v$、および（オプションで）関節トルク $\tau$ と外部力 $w_\text{ext}$。

`externalwrenches` 引数は、`Mechanism` のボディに作用する追加の力を指定するために使用できます。

`stabilization_gains` キーワード引数は、非木構造（ループ）関節の分離を防ぐために使用できるバウムガルテ安定化のPDゲインを設定するために使用できます。詳細については、Featherstone (2008) のセクション 8.3を参照してください。ゲインを指定するためのいくつかのオプションがあります：

  * `nothing` を使用して、バウムガルテ安定化を完全に無効にすることができます。
  * ゲインは、メカニズムの非木構造関節の `JointID` にマッピングされた任意の `AbstractDict{JointID, <:RigidBodyDynamics.PDControl.SE3PDGains}` を使用して、関節ごとに指定できます。
  * 第二のオプションの特別なケースとして、`RigidBodyDynamics.CustomCollections.ConstDict{JointID}` を渡すことで、すべての関節に同じゲインを使用できます。

[`default_constraint_stabilization_gains`](@ref) 関数が呼び出され、最後のオプションを使用してデフォルトのゲインが生成されます。
