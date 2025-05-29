Wright learning curve method. 

```
struct WrightMethod <: LearningCurveMethod end
```

Introduced by T.P. Wright in 1936 in his seminal work on airplane production cost  analysis (Wright, 1936).  This model observes that with each doubling of cumulative production, the unit cost  decreases by a fixed percentage. It is well‐suited for processes where learning is continuous and  gradual.  

$\text{Cost} = \text{InitialEffort} \times \text{TotalUnits}^{\frac{\log(\text{Learning})}{\log(2)} + 1}$

**When to Use:**  

  * When historical data show a smooth, predictable decline in unit costs as production doubles.

**When to Avoid:**  

  * When cost reductions occur in discrete steps or when the production process experiences structural changes.
