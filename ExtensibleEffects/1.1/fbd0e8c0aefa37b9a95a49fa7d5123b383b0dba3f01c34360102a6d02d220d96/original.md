ContextManagerCombinedHandler(otherhandler)

We can combine ContextManager with any other Handler. This is possible because ContextManager, within eff_flatmap, does not constrain the returned eff of the continuation.
