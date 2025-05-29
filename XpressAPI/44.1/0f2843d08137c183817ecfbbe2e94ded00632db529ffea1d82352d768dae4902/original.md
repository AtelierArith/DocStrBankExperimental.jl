```
XPRS_MCFCUTSTRATEGY
```

Level of Multi-Commodity Flow (MCF) cutting planes separation: This specifies how much aggresively MCF cuts should be separated. (integer)

If the separation of MCF cuts is enabled, Xpress will try to detect a MCF network structure in the problem and, if such a structure is identified, it will separate specific cutting planes exploiting the identified network.

Default value: `-1`

Values: -1 : Automatic - let the Optimizer decide. 0 : Separation of MCF cuts disabled. 1 : Moderate separation of MCF cuts. 2 : Aggressive separation of MCF cuts.
