Representation of a real number $x$ as a dedekind cut.

### Fields

  * `low` : function approximating the number from below. Evaluates to true for every number $< x$.
  * `high` : function approximating the number from above. Evaluates to true for every number $> x$.
  * `mpa` : Cached most precise approximation computed so far. This is a dyadic interval bound $x$ which is updated every time the cut is refined to a higher precision.
