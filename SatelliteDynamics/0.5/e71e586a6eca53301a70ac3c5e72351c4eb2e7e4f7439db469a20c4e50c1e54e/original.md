Step dynamics state to the specified time. Will take as many internal steps as  required to advance the propagator to the correct time. No internal step will  exceed the size specified in the state propagator.

Arguments:

  * `state::EarthInertialState` State vector to propagate
  * `time::Union{Real, Epoch}` Time to propagate internal state too. Can be either

a real number to advance the state by or the Epoch
