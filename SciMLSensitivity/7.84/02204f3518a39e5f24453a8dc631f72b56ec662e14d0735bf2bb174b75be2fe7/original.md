ODEForwardSensitivityFunction{iip,F,A,Tt,OJ,J,JP,S,PJ,TW,TWt,UF,PF,JC,PJC,Alg,fc,JM,pJM,MM,CV} <: AbstractODEFunction{iip}

ODEForwardSensitivityFunction is an internal to the ODEForwardSensitivityProblem which extends the AbstractODEFunction to be used in an ODEProblem, but defines the tools requires for calculating the extra differential equations associated with the derivative terms.

ODEForwardSensitivityFunction is not intended to be part of the public API.
