# Crème Bakery Ordering System — Prototype User Manual

A working demonstration of an online shop, counter point-of-sale and owner dashboard for Crème Russian Bakery (Tema and Spintex branches). 

Link: https://theernestagyemang.github.io/cremerussianbakery.com/

---

## 1. What's in the prototype

| Area | Who uses it | What it does |
|---|---|---|
| **Online shop** | Customers | Browse the menu, design a custom cake, sign up, pay online with mobile money or card, track past orders. |
| **Counter POS** | Cashiers | Ring up walk-in sales at either branch, take cash or mobile money, see live stock per product. |
| **Owner dashboard** | Owner | Revenue, orders, takings by payment method, sales by channel and branch, top sellers, inventory per branch, estimated profit & loss, and a full order list — all filterable by date range and branch. |

Every sale, whether it happens online or at the counter, is written to the same order list and reduces the same stock, so the dashboard always reflects both.

---

## 2. Demo accounts

The shop is open to anyone. Customers create their own account from the **Sign in** button in the shop header.

Staff screens are reached from the **Staff** links in the shop footer and need a staff login:

| Screen | Email | Password |
|---|---|---|
| Counter POS | `cashier@cremebakery.com` | `demo1234` |
| Owner dashboard | `owner@cremebakery.com` | `demo1234` |

On the staff sign-in screen you can simply tap one of the two demo accounts to fill the form in. The owner account can open both the dashboard and the POS; the cashier account can open only the POS; customer accounts cannot open either.

---

## 3. Walkthrough — the customer's side

1. **Browse.** The menu is grouped into whole cakes, honey cake boxes, slices & minis and small bakes. Items that are sold out at both branches show *Sold out today* instead of an Add button.
2. **Custom cakes.** The *Design your own cake* section lets a customer pick occasion, size, flavour, date (at least two days ahead) and an optional edible photo print. The estimated price updates as they choose; *Add to basket* puts it in the basket like any other item.
3. **Basket.** The Basket button (top right) opens a side panel where quantities can be changed. Delivery adds a flat GH₵30; pickup is free.
4. **Sign in.** Checkout requires an account. New customers tap *New here? Create an account* and enter name, email, password and WhatsApp number. Returning customers just sign in. Their details are pre-filled at checkout afterwards.
5. **Checkout.** Choose *Delivery* or *Pickup in store*, confirm the branch (the nearest one for delivery, or the one to collect from), set the date, and pick *Mobile money* or *Card*. Online orders are always paid before the bakery bakes or delivers — there is no cash option online.
6. **Pay.** The Paystack checkout opens (see section 7). When payment succeeds the order is recorded as *Preparing*, stock is reduced at the chosen branch, and a confirmation with the order number and Paystack reference is shown.
7. **My orders.** Once signed in, *My orders* in the header lists that customer's past orders with their status.

---

## 4. Walkthrough — the counter POS

1. From the shop footer, tap **Counter POS** and sign in as the cashier.
2. **Choose the branch** using the Tema / Spintex switch at the top. Stock counts on the tiles are for that branch only. Switching branch clears the current ticket.
3. **Tap products** to add them to the ticket on the right. Tiles show the units left; *Low* tiles have four or fewer, *Sold out* tiles are greyed out. Use the − / + controls on the ticket to change quantities.
4. **Take payment.** Choose *Cash* or *MoMo*. For cash, type the amount given and the change due is calculated.
5. **Complete sale.** The sale is recorded immediately, stock at that branch is reduced, and the ticket number advances. The sale appears on the owner dashboard straight away.

Use *View shop* in the top bar to see the customer site, or *Sign out* to leave.

---

## 5. Walkthrough — the owner dashboard

1. From the shop footer, tap **Owner dashboard** and sign in as the owner.
2. **Filters** (top right):
   - *All branches / Tema / Spintex* — every number on the page respects this. The branch list in the left sidebar does the same.
   - *Today / 7 days / 30 days / 90 days* presets, or type any custom *from* / *to* date range.
   - The subtitle under *Overview* confirms exactly what you're looking at, and each figure is compared with the equivalent period before it.
3. **Headline figures.** Revenue, number of orders, average order value, and today's takings with the count of online orders still being prepared.
4. **Revenue by day.** Hover or tap a bar for the exact amount; the best day in the range is highlighted.
5. **Takings by payment / channel / branch.** Where the money is coming from: cash vs mobile money vs card, online vs counter, and Tema vs Spintex.
6. **Top sellers** by revenue for the chosen range.
7. **Inventory.** With *All branches* selected you see a column per branch; low (≤4) and sold-out figures are highlighted. Select one branch to see just its stock.
8. **Profit & loss (estimated).** Revenue, less ingredient and packaging cost (a recipe cost set per product), gives gross profit and margin; wages, rent and utilities are prorated to the date range for an estimated net profit.
9. **Recent orders.** The latest orders in range with customer, items, branch, channel, payment method, status and total.

*Counter POS* in the top bar jumps straight to the till without signing in again.

---


## 6. Where the data lives (important for demos)

This is a static page with no server, so it cannot write to a file on the host. Instead the prototype keeps its data — customer accounts, orders, stock levels and who is signed in — in the **browser's own storage** on the device being used.

What that means in practice:

- Data survives closing the tab and reloading the page.
- Data is **per device and per browser**. An order placed on your phone will not appear on a laptop's dashboard. For a live pitch, do the whole loop (place an order, ring up a sale, open the dashboard) on one device.
- The 90 days of sample sales history is regenerated each day so the charts always end on today's date. Anything you added yourself is kept only for that day.
- Customer passwords are stored as plain text in the browser for demonstration only. Do not use real passwords.
- **Reset demo data** in the shop footer clears everything back to the starting sample and reloads — use it before a presentation.

The production version replaces this with a proper shared database so every device, branch and user sees the same live figures.

---

## 7. Suggested 60-second pitch demo

1. Open the shop, add a *Honey Cake Box* to the basket, check out as a new customer with mobile money. Note the confirmation and reference.
2. Footer → *Owner dashboard* → sign in. Point out the new order at the top of *Recent orders* and that the box's stock at that branch has dropped.
3. Top bar → *Counter POS*. Switch to Spintex, tap two products, take cash, complete the sale.
4. Top bar → back to the dashboard. Change the branch filter to *Spintex*, then *All branches*, and flip between *Today* and *30 days*.

The message: one system, every sale, every branch, live.

---

## 8. What the full build adds

The prototype shows the experience; the production system adds what a demo can't: a shared database across all devices and branches, real staff accounts managed by the owner, Paystack payment verification and refunds on the server, WhatsApp/SMS order notifications, printable receipts and end-of-day reports, product photo uploads, ingredient-level stock, and an admin area for editing products, prices and branches without touching code.
