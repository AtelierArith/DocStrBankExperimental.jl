Parse julia code into a [`MamdaniFuzzySystem`](@ref). See extended help for an example.

# Extended help

### Example

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

# output

tipper

Inputs:
-------
service ∈ [0, 10] with membership functions:
    poor = GaussianMF{Float64}(0.0, 1.5)
    good = GaussianMF{Float64}(5.0, 1.5)
    excellent = GaussianMF{Float64}(10.0, 1.5)

food ∈ [0, 10] with membership functions:
    rancid = TrapezoidalMF{Int64}(-2, 0, 1, 3)
    delicious = TrapezoidalMF{Int64}(7, 9, 10, 12)


Outputs:
--------
tip ∈ [0, 30] with membership functions:
    cheap = TriangularMF{Int64}(0, 5, 10)
    average = TriangularMF{Int64}(10, 15, 20)
    generous = TriangularMF{Int64}(20, 25, 30)


Inference rules:
----------------
(service is poor ∨ food is rancid) --> tip is cheap
service is good --> tip is average
(service is excellent ∨ food is delicious) --> tip is generous


Settings:
---------
- ProdAnd()
- ProbSumOr()
- ProdImplication()
- ProbSumAggregator()
- BisectorDefuzzifier(100)
```
