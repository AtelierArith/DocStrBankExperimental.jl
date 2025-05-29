# WaterLily.jl

[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://WaterLily-jl.github.io/WaterLily.jl/dev/) [![Examples](https://img.shields.io/badge/view-examples-blue.svg)](https://github.com/WaterLily-jl/WaterLily-Examples/) [![CI](https://github.com/WaterLily-jl/WaterLily.jl/workflows/CI/badge.svg?branch=master&event=push)](https://github.com/WaterLily-jl/WaterLily.jl/actions) [![codecov](https://codecov.io/gh/WaterLily-jl/WaterLily.jl/branch/master/graph/badge.svg?token=8XYFWKOUFN)](https://codecov.io/gh/WaterLily-jl/WaterLily.jl)

![Julia flow](assets/julia.gif)

## 概要

**WaterLily.jl** は、純粋なJuliaで書かれたシンプルで高速な流体シミュレーターです。このプロジェクトは、Julia科学コミュニティ内で開発された素晴らしいライブラリによってサポートされており、流体シミュレーションの加速と強化を目指しています。JuliaCon2024の講演をこちらでご覧ください：

[![JuliaCon2024 still and link](assets/JuliaCon2024.png)](https://www.youtube.com/watch?v=FwMh2rq9kOU)

WaterLilyを研究に使用した場合は、ぜひ**引用してください**！[2024年の論文](https://physics.paperswithcode.com/paper/waterlily-jl-a-differentiable-and-backend)では、ソルバーの主な機能を説明し、ベンチマーク、検証、およびプロファイリングの結果を提供しています。

```
@misc{WeymouthFont2024,
    title         = {WaterLily.jl: A differentiable and backend-agnostic Julia solver to simulate incompressible viscous flow and dynamic bodies},
    author        = {Gabriel D. Weymouth and Bernat Font},
    url           = {https://arxiv.org/abs/2407.16032},
    eprint        = {2407.16032},
    archivePrefix = {arXiv},
    year          = {2024},
    primaryClass  = {physics.flu-dyn}
}
```

## 方法/機能

WaterLilyは、カートesianグリッド上で非定常不可圧縮2Dまたは3D [ナビエ-ストークス方程式](https://en.wikipedia.org/wiki/Navier%E2%80%93Stokes_equations) を解きます。圧力ポアソン方程式は、[幾何学的マルチグリッド](https://en.wikipedia.org/wiki/Multigrid_method)法で解かれます。固体境界は、[境界データ浸漬法](https://eprints.soton.ac.uk/369635/)を使用してモデル化されます。ソルバーは、シリアルCPU、マルチスレッドCPU、またはGPUバックエンドで実行できます。

## 例：円の上の流れ

WaterLilyでは、ユーザーがドメインサイズと境界条件、流体の粘度（[レイノルズ数](https://en.wikipedia.org/wiki/Reynolds_number)を決定する）、および固体障害物を浸漬することができます。多くの例、ノートブック、およびチュートリアルは、[WaterLily-Examples](https://github.com/WaterLily-jl/WaterLily-Examples)リポジトリにあります。ここでは、円の上の流れをシミュレーションしてプロットすることで基本を説明します。

シミュレーションドメインのサイズを `n` x `m` セルとして定義します。円の半径は `m/8` で、中心は `(m/2,m/2)` にあります。流れの境界条件は `(U,0)` で、`U=1` を設定し、レイノルズ数は `Re=U*radius/ν` で、`ν`（ギリシャ文字の「ヌ」U+03BD、ラテン小文字の「v」ではない）は流体の運動粘度です。

```julia
using WaterLily
function circle(n,m;Re=100,U=1)
    # 円への符号付き距離関数
    radius, center = m/8, m/2-1
    sdf(x,t) = √sum(abs2, x .- center) - radius

    Simulation((n,m),   # ドメインサイズ
               (U,0),   # ドメイン速度（および速度スケール）
               2radius; # 長さスケール
               ν=U*2radius/Re,     # 流体の粘度
               body=AutoBody(sdf)) # 幾何
end
```

円の幾何は、[符号付き距離関数](https://en.wikipedia.org/wiki/Signed_distance_function#Applications)を使用して定義されます。`AutoBody`関数は、[自動微分](https://github.com/JuliaDiff/)を使用して、体の他の幾何学的パラメータを自動的に推測します。円の距離関数を他のものに置き換えると、今度は他の何かの周りの流れが得られます... 例えば、[ドーナツ](https://github.com/WaterLily-jl/WaterLily-Examples/blob/main/examples/ThreeD_Donut.jl)や[Juliaロゴ](https://github.com/WaterLily-jl/WaterLily-Examples/blob/main/examples/TwoD_Julia.jl)などです。より複雑な幾何には、[ParametricBodies.jl](https://github.com/WaterLily-jl/ParametricBodies.jl)が、スプラインなどの任意のパラメトリック曲線を使用して`body`を定義します。そのリポジトリ（および上記のビデオ）には、例があります。

上記のコードブロックは、定義したパラメータを持つ`Simulation`を返します。これで、シミュレーションを初期化（最初の行）し、時間を進めることができます（2行目）。

```julia
circ = circle(3*2^5,2^6)
sim_step!(circ)
```

`n,m`を2の累乗の倍数に設定したことに注意してください。これは（非常に高速な）幾何学的マルチグリッドソルバーを使用する際に重要です。

これで、好きな変数にアクセスしてプロットできます。例えば、次のようにして速度場のx成分をプロットできます。

```julia
using Plots
u = circ.flow.u[:,:,1] # 最初の成分はx
contourf(u') # プロット用に配列を転置
```

![Initial velocity field](assets/u0.png)

ご覧の通り、円の内部の速度はゼロで、円から遠く離れた速度は1であり、円の周りには加速および減速領域があります。`sim_step!`はわずか1回の時間ステップを実行しただけで、この円の周りの初期流れは、粘性境界層がまだ分離していないため、ポテンシャルフローに似ています。

一連の[流れのメトリック関数](https://github.com/WaterLily-jl/WaterLily.jl/blob/master/src/Metrics.jl)が実装されており、これを使用してシミュレーションを測定できます。次のコードブロックは、シミュレーションを時間`t`まで進め、その後`pressure_force`メトリックを使用して浸漬された体にかかる力を測定する関数を定義します。この関数は時間範囲に適用され、力がプロットされます。

```Julia
function get_forces!(sim,t)
    sim_step!(sim,t,remeasure=false)
    force = WaterLily.pressure_force(sim)
    force./(0.5sim.L*sim.U^2) # 力をスケール！
end

# 時間範囲を通じてシミュレーションし、力を取得
time = 1:0.1:50 # 時間スケールはsim.L/sim.U
forces = [get_forces!(circ,t) for t in time];

# プロット
plot(time,[first.(forces), last.(forces)],
    labels=permutedims(["drag","lift"]),
    xlabel="tU/L",
    ylabel="圧力力係数")
```

![Pressure forces](assets/forces.png)

u-速度の代わりに渦度場をプロットして、後流のスナップショットを確認することもできます。

```julia
# ドメイン内の渦度を計算するためにcurl(velocity)を使用
ω = zeros(size(u));
@inside ω[I] = WaterLily.curl(3,I,circ.flow.u)*circ.L/circ.U

# プロット
clims = (-6,6)
contourf(clamp.(ω,clims...)'; clims,
    color=palette(:RdBu,9),linewidth=0,levels=8,
    aspect_ratio=:equal,border=:none)
```

![Vorticity field](assets/vort.png)

ご覧の通り、WaterLilyは流れが非定常であることを正しく予測しており、交互の渦街後流が発生し、振動する側方力と抗力を引き起こしています。

## マルチスレッドおよびGPUバックエンド

WaterLilyは、[KernelAbstractions.jl](https://github.com/JuliaGPU/KernelAbstractions.jl)を使用してCPUでマルチスレッドを行い、GPUバックエンドで実行します。実装方法とスピードアップは、[2024年の論文](https://physics.paperswithcode.com/paper/waterlily-jl-a-differentiable-and-backend)に記載されており、自由度と時間ステップあたりのコストは1.44ナノ秒まで測定されています！

マルチスレッドを使用するには、*Juliaを`--threads`引数で起動する必要があります。マニュアルの[マルチスレッドセクション](https://docs.julialang.org/en/v1/manual/multi-threading/)を参照してください。複数のスレッドでJuliaを実行している場合、KernelAbstractionsはこれを検出し、ループを自動的にマルチスレッド化します。

GPUで実行するには、`Simulation`メモリをGPU上で初期化する必要があり、視覚化のためにデータをCPUに戻す際には注意が必要です。例として、**3D** GPUシミュレーションの球体と、上で定義した**2D**マルチスレッドCPU円を比較してみましょう。

```Julia
using CUDA,WaterLily
function sphere(n,m;Re=100,U=1,T=Float64,mem=Array)
    radius, center = m/8, m/2-1
    body = AutoBody((x,t)->√sum(abs2, x .- center) - radius)
    Simulation((n,m,m),(U,0,0), # 3D配列サイズとBC
                2radius;ν=U*2radius/Re,body, # 変更なし
                T,   # 浮動小数点型
                mem) # メモリ型
end

@assert CUDA.functional()      # あなたのCUDA GPUは動作していますか？
GPUsim = sphere(3*2^5,2^6;T=Float32,mem=CuArray); # 3D GPUシミュレーション！
println(length(GPUsim.flow.u)) # 1.3M自由度！
sim_step!(GPUsim)              # GPUコードをコンパイルして1ステップ実行
@time sim_step!(GPUsim,50,remeasure=false) # 40s!!

CPUsim = circle(3*2^5,2^6);    # 2D CPUシミュレーション
println(length(CPUsim.flow.u)) # 0.013M自由度！
sim_step!(CPUsim)              # GPUコードをコンパイルして1ステップ実行
println(Threads.nthreads())    # 私は8スレッドを使用しています
@time sim_step!(CPUsim,50,remeasure=false) # 28s!!
```

ご覧の通り、3D球体のセットアップは2D円とほぼ同じですが、3D配列を使用するため、自由度は約1.3Mで、2Dの100倍です。それにもかかわらず、シミュレーションはGPU上で非常に高速で、8スレッドのCPU上のはるかに小さい2Dシミュレーションよりも約40%遅いだけです。[2024年の論文](https://physics.paperswithcode.com/paper/waterlily-jl-a-differentiable-and-backend)や[例のリポジトリ](https://github.com/WaterLily-jl/WaterLily-Examples)には、AMD GPUでの実行を含む、より多くの非自明な例が含まれています。

最後に、KernelAbstractionsは各ループに対していくつかのCPU割り当てを発生させますが、`sim_step!`は完全に非割り当てです。これは、シミュレーションのサイズが大きくなるにつれてスピードアップが改善される理由の1つです。

## 貢献と問題

新しい貢献を常に歓迎しますので、[プルリクエストを送信](https://github.com/WaterLily-jl/WaterLily.jl/compare)して、変更を加えてWaterLilyをさらに良くする手助けをしてください！貢献は、ベンチマーク結果とともに提出する必要があります - WaterLilyは常に高速であるべきです！😃 これには、パフォーマンステストを実施する[完全自動ベンチマークスイート](https://github.com/WaterLily-jl/WaterLily-Benchmarks)があります。簡単に言うと、最新のWaterLilyと変更を比較するには、そのリポジトリをクローンし、次のコマンドでベンチマークを実行します。

```sh
git clone https://github.com/WaterLily-jl/WaterLily-Benchmarks && cd WaterLily-Benchmarks
sh benchmark.sh -wd "<your/waterlily/path>" -w "<your_waterlily_branch> master"
julia --project compare.jl
```

これにより、CPUおよびGPUバックエンドのベンチマークが実行されます。GPUを持っていない場合は、`benchmark.sh`を実行する際に単に`-b "Array"`を渡してください。ベンチマークスイートに関する詳細は、その[README](https://github.com/WaterLily-jl/WaterLily-Benchmarks/blob/main/README.md)にあります。

もちろん、アイデア、提案、質問も歓迎です！これらのいずれかに対処するために[問題を提起](https://github.com/WaterLily-jl/WaterLily.jl/issues/new/choose)してください。

## 開発目標

  * 3Dメッシュで定義された障害物の浸漬 ([Meshing.jl](https://github.com/JuliaGeometry/Meshing.jl))
  * マルチCPU/GPUシミュレーション (https://github.com/WaterLily-jl/WaterLily.jl/pull/141)
  * ([Volume-of-Fluid](https://github.com/TzuYaoHuang/WaterLily.jl/blob/master/src/Multiphase.jl))または他の方法による自由表面物理。
