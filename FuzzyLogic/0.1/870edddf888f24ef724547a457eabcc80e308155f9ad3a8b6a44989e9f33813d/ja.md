Juliaコードを[`MamdaniFuzzySystem`](@ref)に解析します。例については拡張ヘルプを参照してください。

# 拡張ヘルプ

### 例

```jldoctest
fis = @mamfis function tipper(service, food)::tip
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
      cheap = TriangularMF(0, 5, 10)
      average = TriangularMF(10, 15, 20)
      generous = TriangularMF(20, 25, 30)
    end

    and = ProdAnd
    or = ProbSumOr
    implication = ProdImplication

    service == poor || food == rancid --> tip == cheap
    service == good --> tip == average
    service == excellent || food == delicious --> tip == generous

    aggregator = ProbSumAggregator
    defuzzifier = BisectorDefuzzifier
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
    cheap = TriangularMF{Int64}(0, 5, 10)
    average = TriangularMF{Int64}(10, 15, 20)
    generous = TriangularMF{Int64}(20, 25, 30)


推論ルール:
----------------
(service is poor ∨ food is rancid) --> tip is cheap
service is good --> tip is average
(service is excellent ∨ food is delicious) --> tip is generous


設定:
---------
- ProdAnd()
- ProbSumOr()
- ProdImplication()
- ProbSumAggregator()
- BisectorDefuzzifier(100)
```
