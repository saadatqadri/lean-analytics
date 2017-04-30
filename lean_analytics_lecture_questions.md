## Lean Analytics -- Bloom db questions

### How many visits/day is this eCommerce store getting?

```
select date, count(*) as visits
from
customer_purchase_history
group by date;
```

### What is the daily conversion rate for this eCommerce store?

```
select date, cast (purchases as float)/cast(visits as float) from (
select date, count(*) as visits, sum(did_purchase) as purchases
from
customer_purchase_history
group by date
);
```

### What is the total revenue since the store started operations?

```
select sum(purchase_amount) as revenue
from
customer_purchase_history;
```

### What is the revenue / day?

```
select date, sum(purchase_amount) as revenue
from
customer_purchase_history
group by date;
```

