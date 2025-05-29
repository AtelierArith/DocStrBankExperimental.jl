Parse julia code into a [`SugenoFuzzySystem`](@ref). See extended help for an example.

# Extended help

### Example

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
    cheap = 0
    average = food
    generous = 2service + food - 2


Inference rules:
----------------
(service is poor ∧ food is rancid) --> tip is cheap
service is good --> tip is average
(service is excellent ∨ food is delicious) --> tip is generous


Settings:
---------
- ProdAnd()
- ProbSumOr()
```
