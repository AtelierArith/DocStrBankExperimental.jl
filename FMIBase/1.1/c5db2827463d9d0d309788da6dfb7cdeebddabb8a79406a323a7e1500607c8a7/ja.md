```
(fmu::FMU)(;dx::AbstractVector{<:Real},
             y::AbstractVector{<:Real},
             y_refs::AbstractVector{<:fmiValueReference},
             x::AbstractVector{<:Real}, 
             u::AbstractVector{<:Real},
             u_refs::AbstractVector{<:fmiValueReference},
             p::AbstractVector{<:Real},
             p_refs::AbstractVector{<:fmiValueReference},
             ec::AbstractVector{<:Real},
             t::Real)
```

`FMU`を評価し、コンポーネントの状態`x`、入力`u`および/または時間`t`を設定します。コンポーネントが利用できない場合は、1つが割り当てられます。評価の結果は、システム出力`y`および/または状態導関数`dx`である可能性があります。すべてのオプションがすべてのFMUタイプで利用できるわけではなく、たとえば、状態の設定はCS-FMUではサポートされていません。誤った使用に対してはアサーションが生成されます。

# キーワード

  * `dx`: 状態導関数を格納するための配列。提供されていないが必要な場合は、適切な配列が割り当てられ、返されます。CS-FMUではサポートされていません。
  * `y`: システム出力を格納するための配列。提供されていないが要求された場合は、適切な配列が割り当てられ、返されます。
  * `y_refs`: どのシステム出力が返されるべきかを示す値参照の配列。
  * `x`: 設定される状態を含む配列。CS-FMUではサポートされていません。
  * `u`: 設定される入力を含む配列。
  * `u_refs`: どのシステム入力を設定したいかを示す値参照の配列。
  * `p`: 設定されるFMUパラメータの配列。
  * `p_refs`: どのシステムパラメータの感度を決定する必要があるかを示すパラメータ参照の配列。
  * `ec`: 実数値の暗黙的イベント条件（「イベントインジケーター」）の配列。
  * `t`: 設定されるシステム時間を保持するスカラー値。

# 戻り値（タプルとして）

  * `y::Union{AbstractVector{<:Real}, Nothing}`: システム出力`y`（要求された場合、そうでなければ`nothing`）。
  * `dx::Union{AbstractVector{<:Real}, Nothing}`: システム状態導関数（ME-FMUの場合、そうでなければ`nothing`）。
  * `ec::Union{AbstractVector{<:Real}, Nothing}`: システムイベントインジケーター（ME-FMUの場合、そうでなければ`nothing`）。
