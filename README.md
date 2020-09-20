##Checkout Price Calculation
This exercise implements checkout system to calculate the total cost of a shopping based on a set of pricing rules. 

###Terminologies & Assumptions
- SKU [Stock keeping unit] - Unique identifier of an item. 
- Pricing Strategy changes over time. 
- An item can have more than one pricing rule in the future. 


###Approach 
- Instantiate a LineItem object every time an item is added to the cart to encapsulate quantity, pricing rules and other fields that may come up later. 
- Implement Pricing Strategy as an interface to support different types of pricing rules. Each should be able to calculate price for a given lineItem. 

Questions from exercise:
1. How can these be specified in such a way that the checkout doesn’t know about particular
items and their pricing strategies?

    Checkout does not know about particular item and only sums up the total price for all line items. Any specific price calculation logic is abstracted in line item itself. Checkout additionaly also tracks item to pricing strategy mapping which shold be fetched from external source. [Mentioned in TODO]

2. How can we make the design flexible enough so that we can add new styles of pricing rules
in the future?
    
    Pricing strategy is an interface and can be extended for different types of strategies. 
    

###TODO
- Make all mutations to be threadsafe, this could be considered as low priority since the chances of customer modifying the same cart from multiple devices simultaneously is rare.
- Fetch item specific pricing strategy from external storage instead of keeping static map. 
- Extend Pricing Strategy to different types of Strategies.
- Expand lineItem to include other details such as taxRates, addOns, etc. 
- Expand shopping cart to include other details such as serviceCharge, other fees, etc.
- Add cartSummary to show price breakdown in Checkout. 

###Versions
Java - 11
Gradle - 6.5

###Run Tests
`./gradlew test`

