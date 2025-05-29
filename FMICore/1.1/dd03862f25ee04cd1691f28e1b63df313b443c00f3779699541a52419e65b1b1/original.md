Source: FMISpec2.0.2[p.85]: 3.2.2 Evaluation of Model Equations

The model enters Continuous-Time Mode and all discrete-time equations become inactive and all relations are “frozen”. This function has to be called when changing from Event Mode (after the global event iteration in Event Mode over all involved FMUs and other models has converged) into Continuous-Time Mode.
