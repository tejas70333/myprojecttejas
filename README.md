# myprojecttejas
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;

import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

public class ApiController {

 

    public Map<String, Object> bfhl(@RequestBody List<Object> data) {
        Map<String, Object> response = new HashMap<>();

        //fetch  user details
        String fullName = "John Doe";
        String dob = "17/09/1999";
        String userId = fullName.toLowerCase().replace(" ", "_") + "_" + dob.replace("/", "");

        response.put("user_id", userId);

        // Process input data
        List<Integer> evenNumbers = new ArrayList<>();
        List<Integer> oddNumbers = new ArrayList<>();
        List<Character> alphabets = new ArrayList<>();

        for (Object obj : data) {
            if (obj instanceof Integer) {
                int num = (int) obj;
                if (num % 2 == 0) {
                    evenNumbers.add(num);
                } else {
                    oddNumbers.add(num);
                }
            } else if (obj instanceof String) {
                String str = (String) obj;
                for (char c : str.toCharArray()) {
                    if (Character.isLetter(c)) {
                        alphabets.add(Character.toUpperCase(c));
                    }
                }
            }
        }

        response.put("is_success", true);
        response.put("email_id", "john.doe@example.com");
        response.put("college_roll_number", "123456");
        response.put("even_numbers", evenNumbers);
        response.put("odd_numbers", oddNumbers);
        response.put("alphabets", alphabets);

        return response;
    }
}
