```
rootmeasure(μ::AbstractMeasure)
```

It's sometimes important to be able to find the fix point of a measure under `basemeasure`. That is, to start with some measure and apply `basemeasure` repeatedly until there's no change. That's what this does.
