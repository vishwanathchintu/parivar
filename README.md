# parivar
it is a gift my uncle
/**
 * This is the way classes are defined in Java, the public bit just says it's visible
 * to every other class in the system.
 */
public class Beverage
{
  //These are the attributes (fields) of the class.  It's good practice to make them
  //private so that they can only be accessed from within the class.
  private String name;
  private BigDecimal cost;

  /**
   * This is the constructor, which is used to create instances of the class.  In
   * this case it takes the arguments used to initialize the attributes of the class.
   */
  public Beverage(String name, BigDecimal cost)
  {
    this.name = name;
    this.cost = cost;
  }

  /**
   * This is a getter, which provides access to the attributes from outside of the  
   * class.
   */
  public BigDecimal getCost()
  { 
    return this.cost;
  }

  public String getName()
  { 
    return this.name;
  }
}

public class Order
{
  //This line is assigning an instance of HashMap (a standard data structure class 
  //in Java).  A map is a bit like a dictionary, you have a key in this case the
  //beverage that allows you to look-up another value, the quantity.
  private Map<Beverage, Integer> beverages = new HashMap<Beverage, Integer>();

  public BigDecimal getTotal()
  {
    BigDecimal total = BigDecimal.ZERO;

    //Loop over all the beverages that have been added to the map summing the cost.
    for (Beverage beverage : this.beverages.keySet())
    {
      //Convert the quantity in the map to a BigDecimal needed for the multiply method.
      BigDecimal quantity = new BigDecimal(this.beverages.get(beverage));

      total = total.add(beverage.getCost().multiple(quantity));  
    }

    return total;
  }

  public void add(Beverage beverage, Integer quantity)
  {        
    //Store the quantity against the beverage.
    this.beverages.put(beverage, quantity);  
  }
}
