---
title: "TODO - Your title"
abbrev: "TODO - Abbreviation"
category: info

docname: draft-todo-yourname-protocol-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
area: AREA
workgroup: WG Working Group
keyword:
 - next generation
 - unicorn
 - sparkling distributed ledger
venue:
  group: WG
  type: Working Group
  mail: WG@example.com
  arch: https://example.com/WG
  github: USER/REPO
  latest: https://example.com/LATEST

author:
 -
    fullname: Your Name Here
    organization: Your Organization Here
    email: your.email@example.com

normative:

informative:


--- abstract

TODO Abstract


--- middle

# Introduction

- To: 3GPP-TSG-SA-WG5
- Sender: NETMOD
- Category: For your information
- In reply to: LS on need for modeling isInvariant and SystemCreated in YANG

We thank you for your liaison dated, 2023-03-09, explaining your desire and rationale for the IETF to standardize an "IsInvariant" and "SystemCreated" annotations for use with the YANG language.

We aplogise for the slightly delayed response, but the NETMOD working group has been considering a solution in this area, which although it may not exactly meet your concerns (further details below), we believe that we have a draft that has progressed reasonably far through the IETF publication path and hence we believe now would be a good time for members in your community to review and provide comments on it.  [TODO - Depending on when we plan on sending we should either point them to the WG LC, which we may want to extend, or IETF LC, again, which we may want to ask Mahesh to extend by a couple of weeks to ensure that the external parties have had sufficient time to review].

The proposed solution is a "system-defined" configuration datastore, the latest copy of which can be found at [1].

Regarding 1.2.1 isInvariant:

We are not able to offer an exact solution for standardizing an "isInvariant" extension because of concerns that such an extension would end up breaking the transactional behaviour of NETCONF and RESTCONF.  I.e., to help keep programmatic network managemennt clients simple, there is a very strong desire to always allow a client to migrate a devices state from any valid configuration to any different valid configuration as a single committed configuration change.  Defining a flag such as "isInvariant" that forces clients to make configuration changes in multiple independent steps breaks this transactional behaviour and adds complexity to the client.  Instead, the solution that the WG would propose is the servers are implemented such if it necessary to delete and recreate an object when a field within that object is changed then that instrumentation should be performed automatically by the server and be invisible to the client.

This would, as your liaison indicated, potentially be a traffic impacting change, but it has been observed that many such changes are possible and supported in general network device configuration which has not previously required an 'invariant' behaviour annotation, or break in transactional behavior.  As you indicate, it has also been observed that some vendors do indeed have configuration that exhibits "isInvariant" stlye behavior, but NETMODs goal here is that it would be more desirable to gradually migrate away from such behavior rather than standardize and encourage further proliferation of such behavior that introduces unnecessary complexities to automated management clients.  Instead, it is assummed that clients can be designed and implemented so that they can manage such changes appropriately.  [It may be possible to get consensus for an "inVariant" annotation that only provides documentation to the user.  I.e., the annotation in itself would not be expected to change client configuration operations in anyway, it would only serve as documentation to the user that changing a data-node flagged as isInvariant may cause wider changes to the configuration.  Is it even true that we might get consensus for this?]

Regarding 1.2.2 SystemCreated Classes:

The system datastore defined in [1] provides a similar, but slightly different solution to the problem described by SystemCreated Classes in your letter.  The NETMOD WG believes that that this draft could provide a solution for your problems, whilst preserving NETCONF/YANGs transactional behavior.  Hence, the NETMOD WG asks for 3GPP-TSG-SA-WG5 to review and provide comments on this solution.

We looking forward to hearing back from you,
Kent and Lou

NETMOD chairs, on behalf of NETMOD Working Group

References:
 - [1] (https://datatracker.ietf.org/doc/draft-ietf-netmod-system-config/)


# Conventions and Definitions

{::boilerplate bcp14-tagged}


# Security Considerations

TODO Security


# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
