共通乱数変数、または共通乱数（CRN）と呼ばれるものは、異なるパラメータでシミュレーションを繰り返す際に分散を減少させるための手法です。このアイデアは、1つのシミュレーションのランダム性を記録し、その後の実行で同じ選択を再生することです。この特定の実装では、サンプラーが使用するたびに乱数生成器の状態を保存することによってこれを実現しています。

Xoshiroサンプラーは比較的小さな状態（32バイト）を持ち、サンプラーが乱数を使用するたびに保存されます。このCRNレコーダーはメモリにデータを保存しますが、オペレーティングシステムがそのメモリをディスクに転送する最適化を行うように、メモリマップファイルに保存することもできます。

シミュレーションの再生が最初の記録されたシミュレーションよりも多くの引き出しを使用する場合、何が起こるでしょうか？それらのシミュレーションは新しい乱数生成器から引き出します。これは正確なアプローチではありません。

# 例

目標は、10の異なるパラメータセットでシミュレーションを実行し、異なるパラメータが軌道によって決定される量の平均をどれだけ変化させるかを測定することです。

```julia
using Random: Xoshiro
using CompetingClocks
example_clock = (3, 7)  # 時計IDとして2つの整数のタプルを使用します。
sampler = FirstToFire{typeof(example_clock)}()
crn_sampler = CommonRandomRecorder(sampler, typeof(example_clock), Xoshiro)
for trial_idx in 1:100
    run_simulation(model, crn_sampler)
    reset!(crn_sampler)
end
for param_idx in 1:10
    each_model = modify_model!(model, param_idx)
    run_simulation(each_model, crn_sampler)
    reset!(crn_sampler)
end
```
