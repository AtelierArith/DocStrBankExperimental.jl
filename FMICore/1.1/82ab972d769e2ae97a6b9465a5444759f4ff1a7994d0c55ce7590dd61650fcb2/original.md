Source: FMISpec3.0, Version D5ef1c1: 2.4.7.4. Variable Attributes Enumeration that defines the causality of the variable. Allowed values of this enumeration:

parameter - A data value that is constant during the simulation (except for tunable parameters, see there) and is provided by the environment and cannot be used in connections, except for parameter propagation in terminals as described in Section 2.4.9.2.6. variability must be fixed or tunable. These parameters can be changed independently, unlike calculated parameters. initial must be exact or not present (meaning exact).

calculatedParameter - A data value that is constant during the simulation and is computed during initialization or when tunable parameters change. variability must be fixed or tunable. initial must be approx, calculated or not present (meaning calculated).

input - The variable value can be provided by the importer. [For example, the importer could forward the output of another FMU into this input.]

output -  The variable value can be used by the importer. [For example, this value can be forwarded to an input of another FMU.] The algebraic relationship to the inputs can be defined via the dependencies attribute of <fmiModelDescription><ModelStructure><Output>.

local -  Local variables are:

  * continuous states and their ContinuousStateDerivatives, ClockedStates, EventIndicators or InitialUnknowns. These variables are listed in the <fmiModelDescription><ModelStructure>.
  * internal, intermediate variables or local clocks which can be read for debugging purposes and are not listed in the <fmiModelDescription><ModelStructure>.

Setting of local variables:

  * In Initialization Mode and before, local variables need to be set if they do have start values or are listed as <InitialUnknown>.
  * In super state Initialized, fmi3Set{VariableType} must not be called on any of the local variables. Only in Model Exchange, continuous states can be set with fmi3SetContinuousStates. Local variable values must not be used as input to another model or FMU.

independent - The independent variable (usually time [but could also be, for example, angle]). All variables are a function of this independent variable. variability must be continuous. Exactly one variable of an FMU must be defined as independent.  For Model Exchange the value is the last value set by fmi3SetTime. For Co-Simulation the value of the independent variable is lastSuccessfulTime return by the last call to fmi3DoStep or the value of argument intermediateUpdateTime of fmi3CallbackIntermediateUpdate. For Scheduled Execution the value of the independent variable is not defined. [The main purpose of this variable in Scheduled Execution is to define a quantity and unit for the independent variable.] The initial value of the independent variable is the value of the argument startTime of fmi3EnterInitializationMode for both Co-Simulation and Model Exchange.  If the unit for the independent variable is not defined, it is implicitly s (seconds). If one variable is defined as independent, it must be defined with a floating point type without a start attribute. It is not allowed to call function fmi3Set{VariableType} on an independent variable. Instead, its value is initialized with fmi3EnterInitializationMode and after initialization set by fmi3SetTime for Model Exchange and by arguments currentCommunicationPoint and communicationStepSize of fmi3DoStep for Co-Simulation FMUs. [The actual value can be inquired with fmi3Get{VariableType}.]

structuralParameter - The variable value can only be changed in Configuration Mode or Reconfiguration Mode. The variability attribute must be fixed or tunable. The initial attribute must be exact or not present (meaning exact). The start attribute is mandatory. A structural parameter must not have a <Dimension> element. A structural parameter may be referenced in <Dimension> elements. If a structural parameters is referenced in <Dimension> elements, it must be of type <UInt64> and its start attribute must be larger than 0. The min attribute might still be 0.

The default of causality is local. A continuous-time state or an event indicator must have causality = local or output, see also Section 2.4.8.

[causality = calculatedParameter and causality = local with variability = fixed or tunable are similar. The difference is that a calculatedParameter can be used in another model or FMU, whereas a local variable cannot. For example, when importing an FMU in a Modelica environment, a calculatedParameter should be imported in a public section as final parameter, whereas a local variable should be imported in a protected section of the model.]

The causality of variables of type Clock must be either input or output.

Added prefix "fmi3" to help with redefinition of constans in enums.
