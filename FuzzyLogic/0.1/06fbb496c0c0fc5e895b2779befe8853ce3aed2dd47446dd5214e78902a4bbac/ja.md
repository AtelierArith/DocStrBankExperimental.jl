Juliaコードを[`SugenoFuzzySystem`](@ref)に解析します。例については拡張ヘルプを参照してください。

# 拡張ヘルプ

### 例

```jldoctest
fis = @sugfis function tipper(service, food)::tip
    service := begin
        domain = 0:10
        poor = GaussianMF(0.0, 1.5)
        good = GaussianMF(5.0, 1.5)
        excellent = GaussianMF(10.0, 1.5)
    end

    food := begin
        domain = 0:10
        rancid = TrapezoidalMF(-2, 0, 1, 3)
        delicious = TrapezoidalMF(7, 9, 10, 12)
    end

    tip := begin
        domain = 0:30
        cheap = 0
        average = food
        generous = 2service, food, -2
    end

    service == poor && food == rancid --> tip == cheap
    service == good --> tip == average
    service == excellent || food == delicious --> tip == generous
end

# 出力

tipper

入力:
-------
service ∈ [0, 10] のメンバーシップ関数:
    poor = GaussianMF{Float64}(0.0, 1.5)
    good = GaussianMF{Float64}(5.0, 1.5)
    excellent = GaussianMF{Float64}(10.0, 1.5)

food ∈ [0, 10] のメンバーシップ関数:
    rancid = TrapezoidalMF{Int64}(-2, 0, 1, 3)
    delicious = TrapezoidalMF{Int64}(7, 9, 10, 12)


出力:
--------
tip ∈ [0, 30] のメンバーシップ関数:
    cheap = 0
    average = food
    generous = 2service + food - 2


推論ルール:
----------------
(serviceがpoor ∧ foodがrancid) --> tipはcheap
serviceがgood --> tipはaverage
(serviceがexcellent ∨ foodがdelicious) --> tipはgenerous


設定:
---------
- ProdAnd()
- ProbSumOr()
```
