```
GenericCubicEOS(mixture)
GenericCubicEOS(mixture, PengRobinson())
```

Instantiate a generic cubic equation-of-state for a `MultiComponentMixture` and a specified EOS.

Currently supported choices for second argument:

```
1. `PengRobinson()` (default)
2. `PengRobinsonCorrected()`
3. `ZudkevitchJoffe()`
4. `RedlichKwong()`
5. `SoaveRedlichKwong()`
```
