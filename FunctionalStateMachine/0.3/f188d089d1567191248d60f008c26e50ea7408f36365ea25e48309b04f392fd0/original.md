Run state machine function (as functor).

Notes

  * `timeout::Union{Real,Nothing}` is optional with default `=nothing`.

      * this code is skipped in lowered and llvm code if not used
      * subroutine will use `pollinterval::Real` [seconds] to interrogate during `timeout::Real` [seconds] period.
  * can stop FSM early by using any of the following:

      * `breakafter`, `iterlimit`.
  * Can `injectDelayBefore` a function `st.next` to help with debugging.
  * can print FSM steps with `verbose=true`.

      * `verbosefid::IOStream` is used as destination for verbose output, default is `stdout`.
  * FSM steps and `userdata` can be recorded in standard `history` format using `recordhistory=true`.
  * `housekeeping_cb` is callback to give user access to `StateMachine` internals and opportunity to insert bespoke operations.

Example

```julia
bar!(usrdata) = IncrementalInference.exitStateMachine
foo!(usrdata) = bar!

sm = StateMachine(next=foo!)
usrdata = nothing
while st(usrdata); end
```
