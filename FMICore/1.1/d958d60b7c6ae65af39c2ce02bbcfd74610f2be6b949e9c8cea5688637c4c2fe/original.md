Source: FMISpec3.0, Version D5ef1c1: 2.4.7.4. Variable Attributes Enumeration that defines the time dependency of the variable, in other words, it defines the time instants when a variable can change its value. [The purpose of this attribute is to define when a result value needs to be inquired and to be stored. For example, discrete variables change their values only at event instants (ME) or at a communication point (CS and SE) and it is therefore only necessary to inquire them with fmi3Get{VariableType} and store them at event times.] Allowed values of this enumeration: constant - The value of the variable never changes.

fixed - The value of the variable is fixed after initialization, in other words, after fmi3ExitInitializationMode was called the variable value does not change anymore.

tunable - The value of the variable is constant between events (ME) and between communication points (CS and SE) due to changing variables with causality = parameter and variability = tunable. Whenever a parameter with variability = tunable changes, an event is triggered externally (ME or CS if events are supported), or the change is performed at the next communication point (CS and SE) and the variables with variability = tunable and causality = calculatedParameter or output must be newly computed. [tunable inputs are not allowed, see Table 18.]

discrete - Model Exchange: The value of the variable is constant between external and internal events (= time, state, step events defined implicitly in the FMU). Co-Simulation: By convention, the variable is from a real sampled data system and its value is only changed at communication points (including event handling). During intermediateUpdate, discrete variables are not allowed to change. [If the simulation algorithm notices a change in a discrete variable during intermediateUpdate, the simulation algorithm will delay the change, raise an event with earlyReturnRequested == fmi3True and during the communication point it can change the discrete variable, followed by event handling.]

continuous - Only a variable of type == fmi3GetFloat32 or type == fmi3GetFloat64 can be continuous. Model Exchange: No restrictions on value changes (see Section 4.1.1).

The default is continuous for variables of type <Float32> and <Float64>, and discrete for all other types.

For variables of type Clock and clocked variables the variability is always discrete or tunable.

[Note that the information about continuous states is defined with elements <ContinuousStateDerivative> in <ModelStructure>.]

Added prefix "fmi3" to help with redefinition of constans in enums.
