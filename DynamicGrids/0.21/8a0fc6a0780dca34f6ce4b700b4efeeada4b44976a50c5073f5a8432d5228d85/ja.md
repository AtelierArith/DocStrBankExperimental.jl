![DynamicGrids](https://repository-images.githubusercontent.com/136250713/956b0c00-5cc7-11eb-9814-eed48441d013)

[![](https://img.shields.io/badge/docs-stable-blue.svg)](https://cesaraustralia.github.io/DynamicGrids.jl/stable) [![](https://img.shields.io/badge/docs-dev-blue.svg)](https://cesaraustralia.github.io/DynamicGrids.jl/dev) [![CI](https://github.com/cesaraustralia/DynamicGrids.jl/actions/workflows/ci.yml/badge.svg)](https://github.com/cesaraustralia/DynamicGrids.jl/actions/workflows/ci.yml) [![codecov.io](http://codecov.io/github/cesaraustralia/DynamicGrids.jl/coverage.svg?branch=master)](http://codecov.io/github/cesaraustralia/DynamicGrids.jl?branch=master) [![Aqua.jl Quality Assurance](https://img.shields.io/badge/Aqua.jl-%F0%9F%8C%A2-aqua.svg)](https://github.com/JuliaTesting/Aqua.jl)

DynamicGridsは、セルオートマトンを含む高性能なグリッドベースの空間シミュレーションを構築するための一般化されたフレームワークであり、ランダムジャンプや複数のグリッド間の相互作用など、より広範な動作を許可します。これは、[Dispersal.jl](https://github.com/cesaraustralia/Dispersal.jl)によって生物の拡散プロセスのモデリングに拡張されています。

[DynamicGridsGtk.jl](https://github.com/cesaraustralia/DynamicGridsGtk.jl)はシンプルなライブインターフェースを提供し、[DynamicGridsInteract.jl](https://github.com/cesaraustralia/DynamicGridsInteract.jl)はシミュレーションが実行されている間にモデルパラメータをライブで制御することもできます：手動のパラメータ化とモデル探索のためのリアルタイムの視覚フィードバック。

DynamicGridsは、単一のCPU、スレッド化されたCPU、およびCUDA GPU上でルールを実行できます。シミュレーションの実行時間は通常、秒の分数で測定されます。

![Dispersal quarantine](https://raw.githubusercontent.com/cesaraustralia/DynamicGrids.jl/media/dispersal_quarantine.gif)

*Dispersal.jl、カスタムルール、および[DynamicGridsGtk](https://github.com/cesaraustralia/DynamicGridsGtk.jl)のGtkOuputを使用した、検疫相互作用を伴う拡散シミュレーション。これは、ノートパソコンでのリアルタイムのフレームレートを示しています。*

DynamicGrids.jlシミュレーションは、含まれているライフゲームモデル`Life()`を実行するこのようなスクリプトで実行されます：

```julia
using DynamicGrids, Crayons

init = rand(Bool, 150, 200)
output = REPLOutput(init; tspan=1:200, fps=30, color=Crayon(foreground=:red, background=:black, bold=true))
sim!(output, Life())

# または、最初から定義します（はい、これが実際の全実装です！）
life = Neighbors(Moore(1)) do data, hood, state, I
    born_survive = (false, false, false, true, false, false, false, false, false), 
                   (false, false, true, true,  false, false, false, false, false)
    born_survive[state + 1][sum(hood) + 1]
end
sim!(output, life)
```

![REPL life](https://github.com/cesaraustralia/DynamicGrids.jl/blob/media/life.gif?raw=true)

*ターミナルに直接表示されるライフゲームシミュレーション。*

# 概念

このフレームワークは非常にカスタマイズ可能ですが、シミュレーションがどのように機能するかを定義するいくつかの中心的なアイデアがあります：*グリッド*、*ルール*、および*出力*。

## グリッド

シミュレーションは、単一の`AbstractArray`の`init`から派生した1つまたは複数のグリッド上で実行されます。グリッド（`GridData`タイプ）は、単一の配列ではなく、必要に応じてセルの読み取りと書き込みの独立性を維持するためのソースおよび宛先配列です。これらは特定のパフォーマンス最適化のためにパディングされたり、その他の方法で変更されたりする場合があります。ただし、ブロードキャストされた`getindex`操作は、グリッドが通常の配列であるかのように機能することが保証されています。これは、`step!`を使用して手動でシミュレーションを実行する際に便利です。

### グリッドの内容

グリッドには、通常、何らかの`Number`の単純な値が含まれますが、`SArray`、`FieldVector`、または他のカスタム構造体など、他のタイプも可能です。グリッドは、各セルのすべてのタイムステップで実行される`Rule`によって更新されます。

注意：可変オブジェクト（例：`Array`または任意の`mutable struct`）のグリッドは未定義の動作を持ちます。DynamicGrids.jlは、コストが高いため、フレーム間でグリッドを`deepcopy`しませんので、連続するフレームには同じオブジェクトが含まれます。可変オブジェクトはGPUではまったく機能せず、CPUでは比較的遅くなります。代わりに、配列が必要な場合は通常の不変構造体と`StaticArrays.jl`を使用してください。`@set`を使用してSetfield.jlまたはAccessors.jlで更新し、一般的にオブジェクト指向のアプローチよりも関数型プログラミングアプローチを使用してください。

### Init

`init`グリッドには、シミュレーションを開始するために必要な初期化データが含まれています：配列のタイプ、サイズ、要素のタイプ、および初期条件を提供します：

```julia
init = rand(Float32, 100, 100)
```

`init`グリッドは`Output`に添付できます：

```julia
output = ArrayOutput(init; tspan=1:100)
```

または`sim!`に渡すことができ、`Output`に添付された`init`よりも優先されますが、同じタイプとサイズでなければなりません：

```julia
sim!(output, ruleset; init=init)
```

複数のグリッドの場合、`init`は各`Ruleset`で使用される名前に一致する同じサイズの配列の`NamedTuple`です：

```julia
init = (predator=rand(100, 100), prey=(rand(100, 100))
```

`Rule`に正しいグリッドを処理して渡すことは、DynamicGrids.jlによって自動化されており、コストのかからない抽象化です。`Rule`は、最初の2つの（`R`および`W`）型パラメータを使用して、必要なグリッドとその順序を指定します。

[DimensionalData.jl](https://github.com/rafaqz/DimensionalData.jl)や[GeoData.jl](https://github.com/rafaqz/GeoData.jl)からの次元または空間の`init`グリッドは、モデルを通じて伝播し、明示的な次元を持つ出力を返します。これは、[Plots.jl](https://github.com/JuliaPlots/Plots.jl)を使用して地図として正しくプロットされ、シェイプファイルや観測点を簡単に追加できます。

### 非数グリッド

カスタムおよび非`Number`タイプを含むグリッドは、いくつかの注意点とともに可能です。要素タイプの`Base.zero`を定義する必要があり、パフォーマンスのためにビットタイプであるべきです。タプルは`zero`を定義しません。`Array`はビットタイプではなく、`zero`を定義しません。`StaticArrays.jl`の`SArray`は両方ともであり、グリッドの内容として使用できます。`zero`を定義するカスタム構造体も機能するはずです。

ただし、任意の多値グリッド要素タイプについては、`ImageOutput`で機能するために`DynamicGrids.to_rgb`のメソッドを定義し、`ARGB32`を返す必要があります。また、`REPLoutput`が機能するために`isless`も必要です。スカラー`Real`との乗算と加算の定義が必要です。

## ルール

ルールはシミュレーションを実行するためのパラメータを保持し、グリッド内の各アクティブセルに対して呼び出される`applyrule`メソッドに適用されます。ルールにはいくつかの種類があり（[docs](https://cesaraustralia.github.io/DynamicGrids.jl/stable/#Rules-1)に概説されています）、異なるタイプのルールに特化したメソッドを使用することができ、キャッシュや並列化のより効率的な使用を通じてパフォーマンスを大幅に向上させることができます。ルールは`Ruleset`に収集でき、シミュレーションを制御するための追加の引数を持つことができます：

```julia
ruleset = Ruleset(Life(2, 3); opt=SparseOpt(), proc=CuGPU())
```

複数のルールを`Ruleset`に組み合わせることも、単に`sim!`に直接渡すこともできます。各ルールは、親の各ルールのタイプに応じた最適化を使用して、グリッド全体に対して順番に実行されます：

```julia
ruleset = Ruleset(rule1, rule2; timestep=Day(1), opt=SparseOpt(), proc=ThreadedCPU())
```

## 出力

[出力](https://cesaraustralia.github.io/DynamicGrids.jl/stable/#Output-1)は、シミュレーションを保存または表示する方法です。ニーズに応じて相互に使用できます：`ArrayOutput`は高性能シミュレーションのためのシンプルなストレージ構造です。ほとんどの出力と同様に、`init`配列で初期化されますが、この場合、シミュレーションが実行される前に事前に割り当てる必要があるシミュレーションフレームの数も必要です。

```julia
output = ArrayOutput(init; tspan=1:10)
```

上記の`REPLOutput`は、ターミナルやsshで作業しているときにシミュレーションを確認するのに便利な`GraphicOutput`です：

```julia
output = REPLOutput(init; tspan=1:100)
```

`ImageOutput`は、ColorSchemes.jlを使用してフルカラーの視覚シミュレーションを可能にする最も複雑な出力クラスです。また、上記の検疫シミュレーションで示されているように、カラー合成やレイアウトを使用して複数のグリッドを表示することもできます。

[DynamicGridsInteract.jl](https://github.com/cesaraustralia/DynamicGridsInteract.jl)は、Juno、Jupyter、ウェブページ、またはElectronアプリで使用するためのシミュレーションインターフェースを提供し、[ModelParameters.jl](https://github.com/rafaqz/ModelParameters.jl)を使用してパラメータをライブでインタラクティブに制御します。[DynamicGridsGtk.jl](https://github.com/cesaraustralia/DynamicGridsGtk.jl)は、Gtk用のシンプルなグラフィカル出力です。これらのパッケージは、非グラフィカルなシミュレーションで使用されるときに依存関係を避けるために別々に保たれています。

出力は書き込みも簡単であり、高性能アプリケーションは、メモリ使用量を削減するためにカスタム出力を書くことから利益を得るか、`TransformedOuput`を使用することができます。DynamicGrids.jlのパフォーマンスはキャッシュの相互作用によって支配されるため、メモリ使用量を削減することはポジティブな効果を持ちます。

## 例：森林火災

この例では、古典的な確率的森林火災モデルをいくつかの異なる方法で実装し、それらをベンチマークします。`.gif`出力が機能するためには、ImageMagick.jlがインストールされている必要があります。

まず、隣接セルが燃えている場合に現在のセルを燃やす森林火災アルゴリズムを定義します。死んだセルは再び生き返ることができ、生きているセルは自発的に火がつくことがあります：

```julia
using DynamicGrids, ColorSchemes, Colors, BenchmarkTools

const DEAD, ALIVE, BURNING = 1, 2, 3

neighbors_rule = let prob_combustion=0.0001, prob_regrowth=0.01
    Neighbors(Moore(1)) do data, neighborhood, cell, I
        if cell == ALIVE
            if BURNING in neighborhood
                BURNING
            else
                rand() <= prob_combustion ? BURNING : ALIVE
            end
        elseif cell == BURNING
            DEAD
        else
            rand() <= prob_regrowth ? ALIVE : DEAD
        end
    end
end

# 初期配列と出力を設定します（Gtkウィンドウを使用）
init = fill(ALIVE, 400, 400)
output = GifOutput(init; 
    filename="forestfire.gif", 
    tspan=1:200, 
    fps=25, 
    minval=DEAD, maxval=BURNING, 
    scheme=ColorSchemes.rainbow,
    zerocolor=RGB24(0.0)
)

# シミュレーションを実行し、完了時にgifを保存します
sim!(output, neighbors_rule)
```

![forestfire](https://user-images.githubusercontent.com/2534009/72052469-5450c580-3319-11ea-8948-5196d1c6fd33.gif)

200ステップのシミュレーションのタイミングを測定すると、パフォーマンスは非常に良好です。この特定のCPUは6コアを持ち、すべてを使用することで5.25倍のスピードアップを得ており、良好なスケーリングを示しています：

```julia
bench_output = ResultOutput(init; tspan=1:200)

julia> 
@btime sim!($bench_output, $neighbors_rule);
  477.183 ms (903 allocations: 2.57 MiB)

julia> @btime sim!($bench_output, $neighbors_rule; proc=ThreadedCPU());
  91.321 ms (15188 allocations: 4.07 MiB)
```

また、`SetNeighbors`ルールを使用して、現在のセルが燃えている場合に隣接セルを燃やすアルゴリズムを*反転*することもできます：

```julia
setneighbors_rule = let prob_combustion=0.0001, prob_regrowth=0.01
    SetNeighbors(Moore(1)) do data, neighborhood, cell, I
        if cell == DEAD
            if rand() <= prob_regrowth
                data[I...] = ALIVE
            end
        elseif cell == BURNING
            for pos in positions(neighborhood, I)
                if data[pos...] == ALIVE
                    data[pos...] = BURNING
                end
            end
            data[I...] = DEAD
        elseif cell == ALIVE
            if rand() <= prob_combustion 
                data[I...] = BURNING
            end
        end
    end
end
```

*注意：`add!`を使用していません。代わりに、グリッド値を直接設定しています。これは通常、複数のセルが異なる値を設定する場合にエラーのリスクがあります。ここでは、次のタイムステップで現在生きているセルを燃やすだけです。これが複数回発生しても、結果は同じです。*

この場合（かなりスパースなシミュレーション）、このルールはより速くなります：

```julia
julia> @btime sim!($bench_output, $setneighbors_rule);
  261.969 ms (903 allocations: 2.57 MiB)

julia> @btime sim!($bench_output, $setneighbors_rule; proc=ThreadedCPU());
  65.489 ms (7154 allocations: 3.17 MiB)
```

しかし、スケーリングはあまり良くなく、6コアで3.9倍です。最初の方法は、多くのコアを持つマシンではより良いかもしれません。

最後に、これらのルールをGPU用にわずかに書き換えます。`rand`はGPUカーネル内で利用できませんでしたが、今は利用可能ですが、この方法はより速いことが判明しました！複数のグリッドと`SetGrid`を使用して示すのは興味深いです。

この方法では、`SetGrid`ルールを使用して、`:rand`グリッドの親配列全体に`CUDA.rand!`を呼び出します：

```julia
using CUDAKernels, CUDA

randomiser = SetGrid{Tuple{},:rand}() do randgrid
    CUDA.rand!(parent(randgrid))
end
```

次に、`rand()`の代わりに`:rand`グリッド値を使用してGPU用のNeighborsバージョンを定義します：

```julia
neighbors_gpu = let prob_combustion=0.0001, prob_regrowth=0.01
    Neighbors{Tuple{:ff,:rand},:ff}(Moore(1)) do data, neighborhood, (cell, rand), I
        if cell == ALIVE
            if BURNING in neighborhood
                BURNING
            else
                rand <= prob_combustion ? BURNING : ALIVE
            end
        elseif cell == BURNING
            DEAD
        else
            rand <= prob_regrowth ? ALIVE : DEAD
        end
    end
end
```

GPU用のSetNeighborsバージョン：

```julia
setneighbors_gpu = let prob_combustion=0.0001, prob_regrowth=0.01
    SetNeighbors{Tuple{:ff,:rand},:ff}(Moore(1)) do data, neighborhood, (cell, rand), I
        if cell == DEAD
            if rand <= prob_regrowth
                data[:ff][I...] = ALIVE
            end
        elseif cell == BURNING
            for pos in positions(neighborhood, I)
                if data[:ff][pos...] == ALIVE
                    data[:ff][pos...] = BURNING
                end
            end
            data[:ff][I...] = DEAD
        elseif cell == ALIVE
            if rand <= prob_combustion 
                data[:ff][I...] = BURNING
            end
        end
    end
end
```

GTX 1080 GPUで両方のバージョンをベンチマークします。2つのグリッドを読み書きするオーバーヘッドにもかかわらず、これはさらに速くなります：

```julia
bench_output_rand = ResultOutput((ff=init, rand=zeros(size(init))); tspan=1:200)

julia> @btime sim!($bench_output_rand, $randomiser, $neighbors_gpu; proc=CuGPU());
  30.621 ms (186284 allocations: 17.19 MiB)

julia> @btime sim!($bench_output_rand, $randomiser, $setneighbors_gpu; proc=CuGPU());
  22.685 ms (147339 allocations: 15.61 MiB)
```

つまり、*1.4億回/秒*の速度でルールを実行しています。これらのタイミングは、メモリとキャッシュを使用するために`Int32`または`Int16`のグリッドを使用することで改善できる可能性があります（おそらく10-20％）。しかし、ここで止めておきます。
