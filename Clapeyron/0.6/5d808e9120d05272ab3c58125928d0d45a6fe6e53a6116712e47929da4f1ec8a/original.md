```
NoTranslation(args...) <: TranslationModel
```

## Input Parameters

None

## Description

Default volume translation model for cubic models. it performs no translation:

```
V = V₀ + mixing_rule(cᵢ)
cᵢ = 0 ∀ i
```

## Model Construction Examples

```
# Because this model does not have parameters, all those constructors are equivalent:
translation = NoTranslation()
translation = NoTranslation("water")
translation = NoTranslation(["water","carbon dioxide"])
```
