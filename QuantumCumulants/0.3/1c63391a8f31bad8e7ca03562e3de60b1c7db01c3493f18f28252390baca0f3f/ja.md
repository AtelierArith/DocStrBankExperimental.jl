```
indexed_meanfield(ops::Vector,H::QNumber,J::Vector;
    Jdagger::Vector=adjoint.(J),rates=ones(length(J)))
```

`ops`に含まれるインデックス付き演算子[`IndexedOperator`](@ref)の方程式のセットを、ハミルトニアン`H`の下で、そして`J`に含まれる損失演算子とともに計算します。得られる方程式は、ノイズが無視される量子ランジュバン方程式に相当します。これは、`ops`引数および`J`引数の両方に[`IndexedOperator`](@ref)エンティティを取ることができるように修正された[`meanfield`](@ref)関数のバージョンです。詳細については、[`meanfield`](@ref)を参照してください。

# 引数

*`ops::Vector`: 方程式を計算する演算子。 *`H::QNumber`: システムの可逆的な動力学を記述するハミルトニアン。 *`J::Vector{<:QNumber}`: システムの崩壊演算子を含むベクトル。形式は     $\sum_i J_i^\dagger O J_i - \frac{1}{2}\left(J_i^\dagger J_i O + OJ_i^\dagger J_i\right)$     で、ハイゼンベルグ方程式に追加されます。

# オプション引数

*`Jdagger::Vector=adjoint.(J)`: 崩壊演算子のエルミート共役を含むベクトル。 *`rates=ones(length(J))`: `J`の崩壊演算子に対応する減衰率。 *`multithread=false`: `ops`内のすべての演算子の方程式の導出を`Threads.@threads`を使用してマルチスレッドで行うかどうかを指定します。 *`simplify=true`: 導出された方程式を簡略化するかどうかを指定します。 *`order=nothing`: [`cumulant_expansion`](@ref)がどの`order`に対して行われるかを指定します。     `nothing`の場合、このステップはスキップされます。 *`mix_choice=maximum`: 提供された`order`が`Vector`の場合、`mix_choice`は複数のヒルベルト空間に作用する項に対してどの`order`を優先するかを決定します。 *`iv=ModelingToolkit.t`: システムの独立変数（時間パラメータ）。
