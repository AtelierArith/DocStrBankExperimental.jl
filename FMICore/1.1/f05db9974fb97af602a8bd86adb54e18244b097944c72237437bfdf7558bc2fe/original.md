Source: FMISpec3.0, Version D5ef1c1: 2.2.10. Dependencies of Variables

Enumeration that defines the dependencies a single unknown variable vunknown can have in relation to a known variable vknown. They have the following meaning: dependent - no particular structure, f(.., v_{known,i}, ..)

Only for floating point type unknowns v_{unknown}:

constant - constant factor, c ⋅ v_{known,i} where c is an expression that is evaluated before fmi3EnterInitializationMode is called.

Only for floating point type unknowns v_{unknown} in Event and Continuous-Time Mode (ME) and at communication points (CS and SE), and not for <InitialUnknown> for Initialization Mode:

fixed - fixed factor, p⋅v_{known,i} where p is an expression that is evaluated before fmi3ExitInitializationMode is called.

tunable - tunable factor, p⋅v_{known,i} where p is an expression that is evaluated before fmi3ExitInitializationMode is called and in Event Mode due to event handling (ME) or at a communication point (CS and SE)

discrete - discrete factor, d⋅v_{known,i} where d is an expression that is evaluated before fmi3ExitInitializationMode is called and in Event Mode due to an external or internal event or at a communication point (CS and SE).
