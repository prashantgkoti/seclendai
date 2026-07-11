Locate — Before shorting, a borrower asks the broker to identify if he could lend 50k shares of Google or Tesla?. The desk checks inventory/availability and responds with quantity + indicative rate. → locate_requests table.

Availability / Inventory — What the lending desk can actually lend, aggregated from lendable portfolios after removing the different type of restrictions. → inventory table.

GC vs Special — General Collateral stocks are easy to borrow (fee ~25–50 bps). Specials are hard to borrow (fee can be 5%–100%+ annualized, e.g., heavily shorted meme stocks). → securities.hard_to_borrow_flag, fee_bps.

Rebate Rate — With cash collateral: lender reinvests the cash and pays the borrower a rebate. fee = benchmark_rate − rebate_rate. Deeply negative rebate = very hard to borrow. → loans.rebate_rate_bps.

Collateral & Margin — Loan is marked-to-market daily. If collateral value / loan value drops below the required margin (e.g., 102%), a margin call goes out and the borrower has to pay up additionl amount. → collateral, margin_calls tables.

Recall — Lender wants shares back (e.g., beneficial owner sold the position, or wants to vote in an AGM). Borrower has standard settlement cycle (T+1 US) to return, else buy-in risk. → recalls table.

Corporate Actions — Dividends on loaned shares: borrower pays lender a manufactured dividend (a substitute payment). Splits/mergers result in additional quantities that rebooked as loan. → corporate_actions table.

Fails — Settlement fails when shares aren't delivered. A big driver of borrowing demand. → settlement_fails table.

MSLA/GMSLA — The master agreement. Key clauses: collateral eligibility, margin percentages, default/close-out, manufactured payments, recall notice periods, buy-in rights. → your document corpus for RAG.

Utilization — Percentage of lendable inventory currently on loan. High utilization + rising fee = squeeze signal. → computed metric.

Term vs Open loans — Open loans are callable daily; term loans have a fixed end date. → loans.term_type.

Short Interest — Total shares sold short; desks watch it to anticipate borrow demand. → market_data table.