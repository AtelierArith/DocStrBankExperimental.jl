```
kalman(Continuous, A, C, R1, R2)
kalman(Discrete, A, C, R1, R2; direct = false)
kalman(sys, R1, R2; direct = false)
```

線形ガウスモデルの最適漸近カルマンゲインを計算します。

$$
\begin{aligned}
dx &= Ax + Bu + w \\
y &= Cx + v
\end{aligned}
$$

ここで、`w` は共分散 `R1` を持つ動的ノイズであり、`v` は共分散 `R2` を持つ測定ノイズです。

`direct = true` の場合、オブザーバゲインは `(A, CA)` のペアに対して計算されます。これは、[`observer_controller`](@ref) のオプション `direct = true` と一緒に使用することを意図しています。参考文献: "Computer-Controlled Systems" pp 140。`direct = false` は時折「遅延」推定器と呼ばれ、`direct = true` は「現在」推定器です。

連続時間LQG問題の離散時間近似を得るには、関数 [`c2d`](@ref) を使用して対応する離散時間共分散行列を取得できます。

カルマンフィルタを表すLTISystemを取得するには、得られたカルマンフィードバックゲインを [`observer_filter`](@ref) に渡します。LQGコントローラを取得するには、得られたカルマンフィードバックゲインと、[`lqr`](@ref) を使用して計算された状態フィードバックゲインを [`observer_controller`](@ref) に渡します。

`args...; kwargs...` はリカッティソルバーに送信され、クロス共分散などの指定を可能にします。詳細については `?MatrixEquations.arec/ared` を参照してください。

# FAQ

この関数には以下が必要です。

  * `R1` は正半定値でなければなりません
  * `R2` は正定値でなければなりません
  * ペア `(A,R1)` は虚数軸（連続）/ 単位円（離散）上に制御不能なモードを持ってはいけません。例えば、`R1` に影響を受けない積分モードがあってはいけません。この条件が満たされない場合、「ハミルトニアン行列は二分的ではありません」というエラーが発生する可能性があります。
