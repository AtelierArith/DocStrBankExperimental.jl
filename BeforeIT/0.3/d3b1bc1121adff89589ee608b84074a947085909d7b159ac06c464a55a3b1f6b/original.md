```
step!(model; multi_threading = false)
```

This function simulates a single epoch the economic model, updating various components of the model based  the interactions between different economic agents. It accepts a `model` object, which encapsulates the state for the simulation, and an optional boolean parameter `multi_threading` to enable or disable multi-threading.

Key operations performed include:

  * Financial adjustments for firms and banks, including insolvency checks and profit calculations.
  * Economic expectations and adjustments, such as growth, inflation, and central bank rates.
  * Labor and credit market operations, including wage updates and loan processing.
  * Household economic activities, including consumption and investment budgeting.
  * Government and international trade financial activities, including budgeting and trade balances.
  * General market matching and accounting updates to reflect changes in economic indicators and positions.

The function updates the model in-place and does not return any value.
