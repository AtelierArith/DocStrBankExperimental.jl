```julia
simulate(state0, final_time; ...)
simulate(
    state0,
    final_time,
    control!;
    Δt,
    stabilization_gains
)

```

基本的な `Mechanism` シミュレーション：初期状態 `state0` から時間 $0$ から `final_time` まで状態を統合します。これらの時刻での時間の `Vector` と構成ベクトルおよび速度ベクトルの `Vector` を返します。

オプションとして、関数（または他の呼び出し可能なもの）を第3引数（`control!`）として渡すことができます。`control!` はシミュレーションの各時間ステップで呼び出され、時間と `Mechanism` の状態に基づいて関節トルクを指定することを可能にします。次のようになります：

```julia
function control!(torques::AbstractVector, t, state::MechanismState)
    rand!(torques) # 例えば
end
```

統合の時間ステップは、`Δt` キーワード引数を使用して指定できます（デフォルトは `1e-4` です）。

`stabilization_gains` キーワード引数は、Baumgarte 安定化のための PD ゲインを設定するために使用でき、非木構造（ループ）関節の分離を防ぐために使用できます。詳細については、Featherstone (2008) のセクション 8.3 を参照してください。ゲインを指定するためのいくつかのオプションがあります：

  * `nothing` を使用して Baumgarte 安定化を完全に無効にすることができます。
  * ゲインは、メカニズムの非木構造関節の `JointID` をその関節のゲインにマッピングする任意の `AbstractDict{JointID, <:RigidBodyDynamics.PDControl.SE3PDGains}` を使用して、関節ごとに指定できます。
  * 第二のオプションの特別なケースとして、`RigidBodyDynamics.CustomCollections.ConstDict{JointID}` を渡すことで、すべての関節に同じゲインを使用できます。

[`default_constraint_stabilization_gains`](@ref) 関数が呼び出され、最後のオプションを使用してデフォルトのゲインを生成します。

`MuntheKaasIntegrator` を使用します。より多くのオプションを持つ低レベルのインターフェースについては、[`RigidBodyDynamics.OdeIntegrators.MuntheKaasIntegrator`](@ref) を参照してください。
