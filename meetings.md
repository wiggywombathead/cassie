# supervisor meeting log

## 2020/02/04
- Met with Matthias to discuss overarching theme of project. Having read around
  the literature somewhat there is little material out there on distributed
  mechanism design for combinatorial auctions, hence to do a project on this
  would require a *lot* of new work on my part.

- Instead pitched the idea of a project on combinatorial auctions with two main
  themes: firstly, a platform to simulate and benchmark different auctions and
  play around with the various parameters; and secondly, a platform on which to
  host auctions, whereby the system decides on the appropriate mechanism to run
  based on the desired metric (revenue, social welfare, etc.), the bids
  submitted (submodular, additive, etc.), and (perhaps) lower bound on the
  approximation factor.

- He recommended I consider writing a web application -- this is the most
  natural platform on which to host such a system, I would say.

- An important factor to consider is the mechanics of submitting bids. In
  single item cases and cases with very few items on offers this is not a
  problem, but the number of bids is obviously exponential in the number of
  items.

### TODO
- Language of implementation
- Usability: how input bids
- Type of application

## 2020/02/11
- We discussed the todos of last week.

- On the subject of collecting bids, I suggested two main ways in which to do
  so: firstly, allow the bidders to be k-minded, meaning they submit k bids,
  one for each subset they would like to receive, and effectively 0 for every
  other subset; secondly, collect a single bid for each item and have the
  program combine these in complex ways. 

- Regarding this second point, Matthias suggested looking at Yahoo's
  "Predictalot" program, which was a program on which to host prediction
  markets. These allow users to bid on outcomes of various events, e.g. the
  winner of the presidential election, and combines them. Hence this is (at
  least superficially) related to combinatorial auctions. Since people are
  betting their money, they also give an indication as to how people "really
  feel" about certain events, which is interesting.

- I agreed that a web application is the most natural platform on which to host
  such an auction. I expressed my desire to implement it in Lisp, not because
  it is a functional language, but just because I want to learn Lisp.

### TODO
- Do my research proposal on this topic and ask Matthias for any help
- Look into Predictalot and blog posts on it for inspiration regarding
  combining bids in complex ways

## 2020/02/18
- Matthias was not in today, so no meeting. Sent him some of my thoughts over
  email; specifically, this was a sort of final outline for the project.

- A player (seller) creates several bets on outcomes they think will happen
  (they have positive expected utility). Then players may trade these bets (the
  right to receive the winnings) until the event takes place. Winnings are paid
  out according to the odds at the time the bet was bought.

- This has an obvious analogue with two-sided combinatorial markets, in which
  sellers sell their bets and buyers bid for them. This provides good
  opportunity to implement and play with some of the theory in the current
  literature, and to ensure we have some nice theoretical guarantees behind
  trades. Perhaps there is an issue in selling bets, since they aren't tangible
  items but rather "ideas". This will need to be considered.

- I am not sure how markets are implemented currently, but it will present a
  nice opportunity to play around with how they _could_ be, e.g. selecting k
  bids/k bundles of bids, etc. Again, good chance to implement some of the
  theory.

- Came across [Augur][Augur] and [PredictIt][PredictIt] while reading around
  the area of prediction markets, so I will have a look at them this week.

[Augur]: https://github.com/AugurProject/augur
[PredictIt]: https://www.predictit.org/

### TODO
- Set out concrete plan of features and roadmap for project -- structure,
  features, core functionality and research to implement

- Finish research proposal on this for Thursday

## 2020/02/25
- Proposal finished and outline of project details given: web application in
  Common Lisp for hosting two-sided combinatorial prediction markets

### TODO
- Read up on how prediction markets are implemented

## 2020/03/03
- No meeting this week: sent Matthias an email explaining that I had little to
  say this week as focus was placed on other pieces of work, given the time
  that writing the research proposal had taken up

## 2020/03/10
- Showed Matthias a [paper][crowdsourcedPDF] I had read on decentralised
  prediction markets: [Crowdsourced Outcome Determination in Prediction
  Markets][crowdsourced]. This could be quite useful to implement as the whole
  idea about _Predictalot_ was removing restrictions on the types of bet you
  can make. If you completely remove the restrictions and leave it to the
  agents to verify the outcome of (potentially ambiguous) bets, then it is much
  more flexible (but perhaps less economically efficient -- opportunity to
  explore this)

- Also discussed the date of the presentation (24/04) and what to include in
  it. Largely it will be a discussion of what the project is, but he advised it
  would be good to have some working code to demonstrate as well

### TODO
- Understand the technical details of the paper, including the theorems and
  their proofs, as it will make it easier to write/talk about

- Start writing up demonstration code and thinking about presentation

[crowdsourcedPDF]: https://arxiv.org/pdf/1612.04885.pdf
[crowdsourced]: https://arxiv.org/abs/1612.04885
