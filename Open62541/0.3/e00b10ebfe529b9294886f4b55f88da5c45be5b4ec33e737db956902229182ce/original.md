```julia
struct UA_AccessControl
```

Fields:

  * `context::Ptr{Nothing}`
  * `clear::Ptr{Nothing}`
  * `userTokenPoliciesSize::UInt64`
  * `userTokenPolicies::Ptr{Open62541.UA_UserTokenPolicy}`
  * `activateSession::Ptr{Nothing}`
  * `closeSession::Ptr{Nothing}`
  * `getUserRightsMask::Ptr{Nothing}`
  * `getUserAccessLevel::Ptr{Nothing}`
  * `getUserExecutable::Ptr{Nothing}`
  * `getUserExecutableOnObject::Ptr{Nothing}`
  * `allowAddNode::Ptr{Nothing}`
  * `allowAddReference::Ptr{Nothing}`
  * `allowDeleteNode::Ptr{Nothing}`
  * `allowDeleteReference::Ptr{Nothing}`
  * `allowBrowseNode::Ptr{Nothing}`
  * `allowTransferSubscription::Ptr{Nothing}`
  * `allowHistoryUpdateUpdateData::Ptr{Nothing}`
  * `allowHistoryUpdateDeleteRawModified::Ptr{Nothing}`
