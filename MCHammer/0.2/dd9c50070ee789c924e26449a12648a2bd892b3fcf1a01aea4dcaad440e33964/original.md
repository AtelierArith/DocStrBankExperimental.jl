Crawford learning curve method.

```
struct CrawfordMethod <: LearningCurveMethod end
```

Derived from discrete cumulative cost analysis methods found in operations research, the Crawford  learning curve (e.g., Crawford, 1982) aggregates individual unit costs—which decrease according to a  power‐law function of the unit index—to yield a total cost. Unlike the smooth curves of Wright and Experience, the Crawford method sums unit‐by‐unit  costs that are reduced based on their position in the production sequence.  

$\text{Cost} = \sum_{i=1}^{\text{TotalUnits}} \text{InitialEffort} \times i^{\frac{\log(\text{Learning})}{\log(2)}}$

**When to Use:**  

  * When you have detailed unit cost data and need a granular, discrete analysis of learning effects.

**When to Avoid:**  

  * When the overall cost trend is continuous and best represented by a smooth curve, in which case  Wright’s or the Experience model might be preferable.
