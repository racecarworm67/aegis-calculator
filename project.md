public class AegisCalculator {

    /**
     * Calculates the shield value of "Aspect's Aegis"
     * @param championLevel The user's current champion level (1-18)
     * @param otherEnemiesNearby The number of *other* enemies nearby (0-4)
     * @return The total shield value from the "Unbreakable Will" passive
     */
    public double calculateUnbreakableWillShield(int championLevel, int otherEnemiesNearby) {

        // Clamp inputs to valid game ranges
        int level = Math.max(1, Math.min(18, championLevel));
        int enemies = Math.max(0, Math.min(4, otherEnemiesNearby));

        // Calculate linear level scaling for the base shield
        // Base + (TotalGain / LevelsToGain) * (CurrentLevel - 1)
        double baseShield = 100.0 + (200.0 / 17.0) * (level - 1);

        // Calculate the bonus multiplier from nearby enemies
        double bonusMultiplier = 1.0 + (0.50 * enemies);

        double totalShield = baseShield * bonusMultiplier;

        return Math.round(totalShield);
    }

    /**
     * This is the main "tester" method that runs our code.
     */
    public static void main(String[] args) {
        // Create an instance of our calculator
        AegisCalculator calculator = new AegisCalculator();

        // --- YOU CAN EDIT THE VALUES BELOW TO TEST! ---

        int testLevel = 12;
        int testEnemies = 4;

        // --- ------------------------------------ ---

        // Run the calculation
        double shield = calculator.calculateUnbreakableWillShield(testLevel, testEnemies);

        // Print the result
        System.out.println("--- Aegis Calculator Test ---");
        System.out.println("Champion Level: " + testLevel);
        System.out.println("Other Enemies Nearby: " + testEnemies);
        System.out.println("Total Shield: " + shield + " HP");
    }
}
