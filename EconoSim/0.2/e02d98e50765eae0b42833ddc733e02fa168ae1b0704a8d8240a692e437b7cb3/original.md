```
struct SuMSy
```

Representation of the parameters of a SuMSy implementation.

  * id: a unique id.
  * guaranteed_income: the periodical guaranteed income.
  * dem*free*buffer: the demurrage free buffer which is allocated to all accounts which have a right to a guaranteed income.
  * dem_settings: the demurrage tiers. This is a list of tuples consisting of a lower bound and a demurrage percentage. The demurrage percentage is applied to the amounts above the lower bound up to the the next higher lower bound. If the demurrage free buffer of an account is larger than 0, all bounds are shifted up with this amount and no demurrage is applied to the amount up to the available demurrage free buffer.

The lower bound of the first tuple is always set to 0.

  * interval: the size of the period after which the next demurrage is calculated and the next guaranteed income is issued.
  * seed: the amount whith which new accounts start.
